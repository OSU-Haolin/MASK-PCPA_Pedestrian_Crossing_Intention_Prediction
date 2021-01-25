# Mask-PCPA: Pedestrian Crossing Prediction  
  
## Notification
OSU-CITR  

## Environment 

python = 3.8  
tensorflow-gpu = 2.2   
numpy, opencv, PIL, matplotlib, etc  
CPU-i7-6700K, GPU-RTX-2070super  

## Dataset Preparation  

Download the [JAAD Annotation](https://github.com/ykotseruba/JAAD) and put `JAAD` file to this project's root directory (as `./JAAD`).  

Download the [JAAD Dataset](http://data.nvision2.eecs.yorku.ca/JAAD_dataset/), and then put the video file `JAAD_clips` into `./JAAD` (as `./JAAD/JAAD_clips`).  

Copy `jaad_data.py` from the corresponding repositories into this project's root directory (as `./jaad_data.py`).  

In order to use the data, first, the video clips should be converted into images. This can be done using script `./JAAD/split_clips_to_frames.sh` following JAAD dataset's instruction.  

Above operation will create a folder called `images` and save the extracted images grouped by corresponding video ids in the `./JAAD/images `folder.  
```
./JAAD/images/video_0001/
				00000.png
				00001.png
				...
./JAAD/images/video_0002/
				00000.png
				00001.png
				...		
...
```
## Training   

Use `train_test.py` script with `config_file`:
```
python train_test.py -c <config_file>
```

For example, to train MASK_PCPA model run:  

```
python train_test.py -c config_files/MASK_PCPA_JAAD.yaml
```  

The script will automatially save the trained model weights, configuration file and evaluation results in `models/<dataset>/<model_name>/<current_date>/` folder.

See comments in the `configs_default.yaml` and `action_predict.py` for parameter descriptions.

Model-specific YAML files contain experiment options `exp_opts` that overwrite options in `configs_default.yaml`.  


## Test saved model  

To re-run test on the saved model use:  

```
python test_model.py <saved_files_path>
```

For example:  
```
python test_model.py models/jaad/MAS_PCPA/xxxx/
```  

## TODO Lists

- [ ] Readme Completion
- [ ] Pretrained Model
- [ ] Support PIE Dataset
