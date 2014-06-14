gokmeans
======

A Go (golang) package that implements the K-means clustering algorithm.

Goroutines are used throughout to do some calulations concurrently.

#### Get package

`go get github.com/mdesenfants/gokmeans`

#### Example

```
package main

import (
	"fmt"
	"github.com/mdesenfants/gokmeans"
)

var observations []gokmeans.Node = []gokmeans.Node {
	gokmeans.Node{20.0, 20.0, 20.0, 20.0},
	gokmeans.Node{21.0, 21.0, 21.0, 21.0},
	gokmeans.Node{100.5, 100.5, 100.5, 100.5},
	gokmeans.Node{50.1, 50.1, 50.1, 50.1},
	gokmeans.Node{64.2, 64.2, 64.2, 64.2},
}

func main() {
	// Get a list of centroids and output the values
	if success, centroids := gokmeans.Train(observations, 2, 50); success {
		// Show the centroids
		fmt.Println("The centroids are")
		for _, centroid := range centroids {
			fmt.Println(centroid)
		}

		// Output the clusters
		fmt.Println("...")
		for _, observation := range observations {
			index := gokmeans.Nearest(observation, centroids)
			fmt.Println(observation, "belongs in cluster", index+1, ".")
		}
	}
}
```
