# Bi-lingual Vision-Language Navigation

We introduce a new dataset for Bi-Lingual Vision-Language Navigation. 

## Bi-lingual Room-to-Room (BL-R2R) Dataset

The BL-R2R dataset is built upon the [R2R](https://arxiv.org/abs/1711.07280) dataset and extends it with Chinese instructions. 
BL-R2R preserves the same splits as in R2R and thus consists of `train`, `val-seen`, and `val-unseen` splits with both English and Chinese instructions, and `test` split with English instructions only.  

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
