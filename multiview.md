# Multiview dataset

This dataset was produced as part of our [FOUND](http://ollieboyne.github.io/FOUND) paper. The code there shows how to load and manipulate this dataset.

The dataset contains a folder for each multiview scan, with the following items:

| Folder/file                         | Data type           | Description                                                                                              |
|-------------------------------------|---------------------|----------------------------------------------------------------------------------------------------------|
| `rgb`                               | Folder, `.jpeg`     | Captured images                                                                                          |
| `norm_gt`                           | Folder, `.png` | Ground truth normals (from rendering `mesh.obj`                                                          |
| `norm_found`                        | Folder, `.png` | Surface normals as predicted in [FOUND](http://ollieboyne.github.io/FOUND)                               |
| `norm_found_unc`                    | Folder, `.png`| Surface normal uncertainty as predicted in [FOUND](http://ollieboyne.github.io/FOUND)                    |
| `normals_colmap`                    | Folder, `.png` | Surface normals reconstructed via [COLMAP](https://colmap.github.io)                                     |
| `mesh.obj`                          | `.obj` | Ground truth 3D scan                                                                                     |
| `colmap_mesh.obj`                   | `.obj` | 3D scan from [COLMAP](https://colmap.github.io)                                                          |
| [`keypoints.json`](#keypoints.json) | `.json` | 2D keypoints as predicted in [FOUND](http://ollieboyne.github.io/FOUND) |
| [`colmap.json`](#colmap.json)       | `.json` | Camera calibration from [COLMAP](https://colmap.github.io)                                               |

## keypoints.json

These are predicted keypoints from a network trained on synthetic data, so their accuracy cannot be guaranteed.

```yaml
{
  "kp_labels": ["big toe", "2nd toe", ...], # N keypoint names
  "annotations":
    {
      <IMG_PATH> : {
                     "kps": [[0., 0., 0.], ...], # [N x 2] Keypoints
                     "vis": [1.0, ...], # N visibility likelihoods (0 - 1)
                     "variance": [[1.0, 1.0], ...] # [N x 2] predicted variance of keypoint positions
                  }
      ...
    }
}
```

## colmap.json

The data here is taken from a [COLMAP](https://colmap.github.io) reconstruction, which has been scaled to match our ground truth meshes.

```yaml
{
  "camera":
    {
      "width": 480, # image width, pixels
      "height": 640, # image height, pixels
      "f": 500, # focal length, pixels
      "cx": 240, # optical centre X, pixels
      "cy": 320, # optical centre Y, pixels
      "k": 0.001, # skew
    },
  "images":
    [
      {
        "image_id": 1, # Used within COLMAP
        "pth": "IMG_6268.jpeg", # filepath of image within rgb folder
        "R": [[...], ...], # [3 x 3] Camera rotation matrix
        "C": [...], # 3 world camera position
        "T": [...], # 3 world camera position in 'R' reference frame
      },
        
      ...
    ]
}
```

All matrices are given in [COLMAP](https://colmap.github.io)'s coordinate system.