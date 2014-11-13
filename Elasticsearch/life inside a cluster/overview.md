ES就是为高可用和可扩展而生的。扩展可以通过购置性能更强的服务器(垂直扩展或者向上扩展，Vertical Scale/Scaling Up)，亦或是通过购置更多的服务器(水平扩展或者向外扩展，Horizontal Scale/Scaling Out)来完成。

尽管ES能够利用更强劲的硬件，垂直扩展毕竟还是有它的极限。真正的可扩展性来自于水平扩展 - 通过向集群中添加更多的节点来分布负载，增加可靠性。

在大多数数据库中，水平扩展通常都需要你对应用进行一次大的重构来利用更多的节点。相反，ES天生就是分布式的：它知道如何管理多个节点来完成扩展和实现高可用性。这也意味着你的应用不需要在乎这一点。

在本章中，我们会介绍如何建立集群(Cluster)，节点(Node)和分片(Shard)来根据你的需求完成扩展，同时也能够保证即使发生硬件故障你的数据也会安然无恙。