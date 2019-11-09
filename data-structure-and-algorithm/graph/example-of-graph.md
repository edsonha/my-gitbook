# Example of Graph

![](../../.gitbook/assets/untitled%20%281%29.jpg)

```text
class Graph {
  constructor() {
    this.numberOfNodes = 0;
    this.adjacentList = {};
  }

  addVertex(node) {
    this.adjacentList[node] = {};
    this.numberOfNodes++;
  }
  addEdge(node1, node2, weight) {
    //undirected Graph
    this.adjacentList[node1][node2] = weight;
    this.adjacentList[node2][node1] = weight;
  }

  showConnections() {
    const allNodes = Object.keys(this.adjacentList);
    for (let node of allNodes) {
      let nodeConnections = Object.keys(this.adjacentList[node]);
      let connections = "";
      let vertex;
      for (vertex of nodeConnections) {
        connections += "\n" + vertex + ": " + this.adjacentList[node][vertex];
      }
      console.log(node + "-->" + connections);
    }
  }
}

const myGraph = new Graph();
myGraph.addVertex("0");
myGraph.addVertex("1");
myGraph.addVertex("2");
myGraph.addVertex("3");
myGraph.addVertex("4");
myGraph.addVertex("5");
myGraph.addVertex("6");
myGraph.addEdge("3", "1", "50");
myGraph.addEdge("3", "4", "25");
myGraph.addEdge("4", "2", "46");
myGraph.addEdge("4", "5", "67");
myGraph.addEdge("1", "2", "12");
myGraph.addEdge("1", "0", "23");
myGraph.addEdge("0", "2", "34");
myGraph.addEdge("6", "5", "45");

myGraph.showConnections();
//Answer:
// 0-->1 2
// 1-->3 2 0
// 2-->4 1 0
// 3-->1 4
// 4-->3 2 5
// 5-->4 6
// 6-->5
```

