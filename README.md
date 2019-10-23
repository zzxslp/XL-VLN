# Cross-lingual Room-to-Room (XL-R2R) Navigation Task


## Data

Data consists of train/val-seen/val-unseen/ splits for English and Chinese pairs, and test split for English instructions.
There are two validation sets to better understand generalization performance between buildings that are in the training set (val-seen) and unseen buildings. The test set consists entirely of unseen buildings. 

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

For the test set, only the first path_id (starting location) is included. There is a test server for scoring uploaded trajectories according to the metrics in the [paper](https://arxiv.org/abs/1711.07280).

There are 7 json files. 4 for English instructions and 3 for Chinese instructions.
