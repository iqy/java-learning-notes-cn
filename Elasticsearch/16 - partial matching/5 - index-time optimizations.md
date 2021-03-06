## 索引期间的优化(Index-time Optimizations) ##

目前我们讨论的所有方案都是在查询期间的。它们不需要任何特殊的映射或者索引模式(Indexing Patterns)；它们只是简单地工作在已经存在于索引中的数据之上。

查询期间的灵活性是有代价的：搜索性能。有时，将这些代价放到查询之外的地方是有价值的。在一个实时的Web应用中，一个额外的100毫秒的延迟会难以承受。

通过在索引期间准备你的数据，可以让你的搜索更加灵活并更具效率。你仍然付出了代价：增加了的索引大小和稍微低一些的索引吞吐量，但是这个代价是在索引期间付出的，而不是在每个查询的执行期间。

你的用户会感激你的。