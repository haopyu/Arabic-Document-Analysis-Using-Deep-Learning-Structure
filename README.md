# Arabic-Document-Analysis-Using-Deep-Learning-Structure

Source codes of our CS591 project: Arabic Document Analysis Using Deep Learning Structure.

**Wenda Qin,** **Hao Yu**

## Faster-R-CNN-based method
A pre-trained model can be downloaded here: 
http://cs-people.bu.edu/wdqin/current_model_nms_05

- training the model:
run Faster-RCNN_based_and_CRAFT_based_processing/creating_masks_for_BCE.ipynb
then run Faster-RCNN_based_and_CRAFT_based_processing/training_detection_model.ipynb
you will need to modify the dataset size in the code as the default number of images in the code is 300. 
- to watch testing results generated by the model:
run Faster-RCNN_based_and_CRAFT_based_processing/Visualizing_the_model.ipynb, you need to specify the model you trained or the pre-trained one.
run Faster-RCNN_based_and_CRAFT_based_processing/Conversion_of_Format.ipynb
the visualized results are shown in Faster-RCNN_based_and_CRAFT_based_processing/results (you might need to change the path correctly 
before doing that)


## CRAFT-based method
The implementation of CRAFT-based method are in the folder craft and segmentation
### Requirements
- PyTorch>=0.4.1
- torchvision>=0.2.1
- opencv-python>=3.4.2
- requirments.txt
```
pip install -r craft/requirements.txt
```

### Generating text detection results

- Download the trained [model](https://drive.google.com/open?id=1Jk4eGD7crsqCCg9C9VjCLkMN3ze8kutZ) which is trained on SynthText, IC13, IC17 dataset.
 
- Run with pretrained model
``` (with python 3.7)
python craft/test.py --trained_model=[weightfile] --test_folder=[folder path to test images]
```

The result images will be saved to `./result` by default.

### Segmentation

- Train
``` (with python 3.7)
python segmentation/main.py --train --input=[folder path to input images] --output=[folder path to output files]
```

- Test
``` (with python 3.7)
python segmentation/main.py --input=[folder path to input images] --output=[folder path to output files]
```
- Merging non-text results from Faster-R-CNN-based method:
run CRAFT_generate_csv.ipynb
run Merging_Text_and_non_text_csvs.ipynb

To visualize the result, 
run Faster-RCNN_based_and_CRAFT_based_processing/Conversion_of_Format.ipynb
the visualized results are shown in Faster-RCNN_based_and_CRAFT_based_processing/results (you might need to change the path correctly 
before doing that)
