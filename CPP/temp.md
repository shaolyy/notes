将对图的攻击和防御扩展到更大的图上是一个挑战。事实上，攻击的和防御的瓶颈可能是在攻击上。
例如Meta攻击方法需要计算完全临界矩阵的梯度，因此不能应用到更大的图上。
例如，在Pubmed实验中，Pro-GNN使用了A-Meta-self来进行非目标攻击，用于节省时间和内存。
我们的框架包含辅助图的构建和图调和。
在构建辅助图的过程中，构建属性图需要计算节点间相似性，并选取K个最大的邻居。
考虑大规模图中特征小于节点数，其时间复杂度为O(N^2+nlogn);
在构建结构图中，我们需要选取节点所有的二阶邻居，其复杂度为O（）。在图调和阶段，时间复杂度与边和节点数量成正比。值得注意的是，这些操作都是在图模型训练之前的预处理阶段，因此虽然复杂度有些为N2，但不是不可以接受。
在联合GCN中，我们使用了额外的辅助图，模型的计算也相应的增加。

Extending attacks and defenses on graphs to larger graphs is a challenge. In fact, the bottleneck of attacking and defense methods on a large-scale graph may be the attacking rather than defense.
For example, the Mettack needs to compute gradients on the full adjacency matrix, and thus cannot be applied to larger graphs.
As a practical example, in the experiment of Pubmed, an approximate version of Meta-Self, A-Meta-Self is applied to save memory and time.
Our framework includes auxiliary graphs construction and graph reconciliation.
In the process of constructing the auxiliary graph, constructing the attribute graph requires calculating the similarity between nodes and selecting the K nearest neighbors for each node.
Considering that the features in a large-scale graph are smaller than the number of nodes, the time complexity is O(N^2+nlogn).

In the process of constructing the structure graph, we need to select all the 2-hop neighbors of each node, and the complexity is O().
In the graph reconciliation phase, the time complexity is proportional to the number of edges and nodes.
It is worth noting that these operations are in the preprocessing stage before the graph model training, and these calculations only need to be performed once.
In the joint GCN, we use additional auxiliary graphs, and the computational complexity of the model increases accordingly.


For the space complexity, we use two additional auxiliary graphs, and the space complexity is O(3N^2).
To compare the efficiency of our method and other defense methods, we verified the training time of the baseline on Pubmed. 
The calculation of the adjacency matrix usually leads to OOM(out of memory) problems. For example, for the Pubmed dataset, Pro-GNN cannot be trained on 16G video memory devices. 
We test all baseline with a device that has a 6-core CPU and 16G memory.