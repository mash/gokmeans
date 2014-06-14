gokmeans
======

A Go (golang) package that implements the K-means clustering algorithm.


#### Example

```
package main

import (
	"fmt"
	"github.com/mdesenfants/kmeans"
)

var observations []kmeans.Node = []kmeans.Node {
	kmeans.Node{20.0, 20.0, 20.0, 20.0},
	kmeans.Node{21.0, 21.0, 21.0, 21.0},
	kmeans.Node{100.5, 100.5, 100.5, 100.5},
	kmeans.Node{50.1, 50.1, 50.1, 50.1},
	kmeans.Node{64.2, 64.2, 64.2, 64.2},
}

func main() {
	// Get a list of centroids and output the values
	if success, centroids := kmeans.Train(observations, 2, 50); success {
		// Show the centroids
		fmt.Println("The centroids are")
		for _, centroid := range centroids {
			fmt.Println(centroid)
		}
		
		// Output the clusters
		fmt.Println("...")
		for _, observation := range observations {
			index := kmeans.Nearest(observation, centroids)
			fmt.Println(observation, "belongs in cluster", index+1, ".")
		}
	}
}

```
