# Motion Planning Networks
Implementation of [MPNet: Motion Planning Networks](https://sites.google.com/view/mpnet). [[arXiv]](https://arxiv.org/abs/1806.05767)  

[![MPNet](https://img.youtube.com/vi/3hQzWDLfDxA/0.jpg)](https://www.youtube.com/watch?v=3hQzWDLfDxA)

The code can easily be adapted for [Informed Neural Sampling](https://arxiv.org/abs/1809.10252).

## Contains
* Data Generation
	* Any existing classical motion planner can be used to generate datasets. However, we provide following implementations in C++:
		* [P-RRT*](https://link.springer.com/article/10.1007/s10514-015-9518-0)
		* [RRT*](https://arxiv.org/abs/1105.1186)
		* Example dataset: [simple2D](https://drive.google.com/open?id=1oADJ85qxb3WKHXE4Bj6lwio-soGOktRa)
* MPNet algorithm

## Requirements
* Data Generation

	1. Install [libbot2]( https://github.com/libbot2/libbot2)
		* Make sure all dependencies of libbot2 (e.g., lcm) are installed.
		* Install libbot2 with the local installation procedure.
		* Run "make" in the data_generation folder where the README file is located.

	2. Use any compiler such as Netbeans to load the precomplie code.
		* data_generation/src/rrts_main.cpp contains the main rrt/prrt code. 	
		* data_generation/viewer/src/viewer_main.cpp contains the visualization code.
			* Also checkout comments in data_generation/viewer/src/renderers/graph_renderer.cpp

		* Note: main_viewer and rrts_main should run in parallel as:
			* rrts_main sends the path solution as well as the tree to the main_viewer to publish through local network.
			* data is transmitted through LCM network protocol.

* MPNet
	* [PyTorch](http://pytorch.org/) 


## Examples

1. Assuming paths to obstacles point-cloud are declared, train obstacle-encoder:
```python MPNET/AE/CAE.py```

2. Assuming paths to demonstration dataset and obstacle-encoder are declared, run mpnet_trainer:
	
    ```python MPNET/train.py```
    
3. Run tests by first loading the trained models:
	
    ```python MPNET/neuralplanner.py``` 

## References

```
@article{qureshi2018motion,
  title={Motion Planning Networks},
  author={Qureshi, Ahmed H and Bency, Mayur J and Yip, Michael C},
  journal={arXiv preprint arXiv:1806.05767},
  year={2018}
}
@article{qureshi2018deeply,
  title={Deeply Informed Neural Sampling for Robot Motion Planning},
  author={Qureshi, Ahmed H and Yip, Michael C},
  journal={arXiv preprint arXiv:1809.10252},
  year={2018}
}
```


