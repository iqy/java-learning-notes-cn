## function_score查询 ##

[function_score查询](http://www.elasticsearch.org/guide/en/elasticsearch/reference/current/query-dsl-function-score-query.html)是处理分值计算过程的终极工具。它让你能够对所有匹配了主查询的每份文档调用一个函数来调整甚至是完全替换原来的_score。

实际上，你可以通过设置过滤器来将查询得到的结果分成若干个子集，然后对每个子集使用不同的函数。这样你就能够同时得益于：高效的分值计算以及可缓存的过滤器。

它拥有几种预先定义好了的函数：

**weight**

对每份文档适用一个简单的提升，且该提升不会被归约：当weight为2时，结果为2 * _score。

**field_value_factor**

使用文档中某个字段的值来改变_score，比如将受欢迎程度或者投票数量考虑在内。

**random_score**

使用一致性随机分值计算来对每个用户采用不同的结果排序方式，对相同用户仍然使用相同的排序方式。

**衰减函数(Decay Function) - linear，exp，gauss**

将像publish_date，geo_location或者price这类浮动值考虑到_score中，偏好最近发布的文档，邻近于某个地理位置(译注：其中的某个字段)的文档或者价格(译注：其中的某个字段)靠近某一点的文档。

**script_score**

使用自定义的脚本来完全控制分值计算逻辑。如果你需要以上预定义函数之外的功能，可以根据需要通过脚本进行实现。

没有function_score查询的话，我们也许就不能将全文搜索得到分值和近因进行结合了。我们将不得不根据_score或者date进行排序；无论采用哪一种都会抹去另一种的影响。function_score查询让我们能够将两者融合在一起：仍然通过全文相关度排序，但是给新近发布的文档，或者流行的文档，或者符合用户价格期望的文档额外的权重。你可以想象，一个拥有所有这些功能的查询看起来会相当复杂。我们从一个简单的例子开始，循序渐进地对它进行介绍。