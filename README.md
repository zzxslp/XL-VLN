# Cross-lingual Vision-Language Navigation

We introduce a new dataset and propose a general learning framework for [Cross-Lingual Vision-Language Navigation](https://arxiv.org/abs/1910.11301). 
First, we explore the possibility of building a cross-lingual agent when no training data of the target language is available. Under the zero-shot learning scenario, our model shows competitive results even compared to a model trained with all target language instructions. We then study and further improve the transferring ability of our model when given a certain amount of target language data. 
Our dataset and methods demonstrate potentials of building scalable cross-lingual agents to serve speakers with different languages.

Please read our paper for more details: https://arxiv.org/abs/1910.11301.

## Cross-lingual Room-to-Room (XL-R2R) Dataset

The XL-R2R dataset is built upon the [R2R](https://arxiv.org/abs/1711.07280) dataset and extends it with Chinese instructions. 
XL-R2R preserves the same splits as in R2R and thus consists of `train`, `val-seen`, and `val-unseen` splits with both English and Chinese instructions, and `test` split with English instructions only.  

Data is formatted as follows:
```
{
  "distance": float,
  "scan": str,
  "path_id": int,
  "path": [str x num_steps],
  "heading": float,
  "instructions": [str x 3],
}
```
- `distance`: length of the path in meters.
- `scan`: Matterport scan id.
- `path_id`: Unique id for this path.
- `path`: List of viewpoint ids (the first is is the start location, the last is the goal location)
- `heading`: Agents initial heading in radians (elevation is always assumed to be zero).
- `instructions`: Three unique natural language strings describing how to find the goal given the start pose.

For the test set, only the first path_id (starting location) is included (a [test server](https://evalai.cloudcv.org/web/challenges/challenge-page/97/overview) is hosted by [Anderson et al.](https://arxiv.org/abs/1711.07280) for scoring uploaded trajectories).
