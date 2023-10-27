# Meshes dataset

The dataset is described in the annotations file `.json`. Structured as shown below:

```yaml
{ 
  'data':
     [
       {
         'Foot ID': '0000',       # ID of foot
         'Scan ID': 'A',          # ID of scan of this foot
         'PNG file': '%.png',     # Location of PNG 4K texture
         'OBJ file': '%.obj',     # Location of .obj file
         'MTL file': '%.mtl',     # Location of .mtl file
         'footedness': 'left',    # Left/right footed
         'pose': ['T-pose'],      # A list of pose descriptions given to users while scanning
         
         # Information about the subject
         'Sex': 'Male',
         'Ethnicity': 'White',
         'Age': 20,
         'Height (cm)': 170
       }, 
       
       ...
       
     ]
}
```

## Acknowledgements

If you make use of this dataset, please cite the following paper:


```
@inproceedings{boyne2022find,
            title={FIND: An Unsupervised Implicit 3D Model of Articulated Human Feet},
            author={Boyne, Oliver and Charles, James and Cipolla, Roberto},
            booktitle={British Machine Vision Conference (BMVC)},
            year={2022}
}
```

## Notes

- **Pose descriptions** - We provide some information about the nature of the pose descriptions in the supplementary of [our paper](https://ollieboyne.github.io/FIND/)
- **Registration** - Our models are only loosely aligned, following the process described in [our paper](https://ollieboyne.github.io/FIND/)