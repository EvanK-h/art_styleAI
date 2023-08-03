# art_styleAI

This model classifies an image of Academic Art, Japanese Art, or Western Medieval Art into one of these three classes. This model can be especially useful for art students trying to classify artworks and find their art style, or for people who are just getting into art and want to know what art style a painting was made in.

## The Algorithm

This model is a re-trained ResNet-18 model which was created on a Jetson Nano and trained on a dataset of Academic Art, Japanese Art, and Western Medieval Art. It runs on an imagenet.py program that will classify a piece of artowork as one of these three art styles.

## Running this project

1. Make sure that both the Jetson Inference library and Python3 are installed on your Jetson Nano.
2. Download the model_best.pth.tar file and the art_styles folder. Link to the files: https://drive.google.com/drive/folders/1n2O--slnZv-2JohwBv1gV1xDk0SCfq6a?usp=sharing
3. Open the terminal on your nano and navigate to the classification directory:
```
   $ cd jetson-inference/python/training/classification
```
4. Create two new directories, data and models:
```
   $ mkdir data
   $ mkdir models
```
5. Navigate to the data directory and create a new directory called art_styles:
```
   $ cd data
   $ mkdir art_styles
```
6. Navigate to the models directory and create a new directory called art_styles:
```
   $ cd ../models
   $ mkdir art_styles
```
7. Upload the model_best.pth.tar file to the art_styles directory in models and upload the art_styles folder to the art_styles directory in data.
8. Navigate to the jetson-inference directory and run the docker:
```
   $ cd ../../../
   $ ./docker/run.sh
```
9. Navigate to the classification directory again:
```
   $ cd python/training/classification
```
10. Export the model to ONNX:
```
   $ python3 onnx_export.py --model-dir=models/art_styles
```
11. Exit the docker and navigate to the classification directory again:
```
   $ exit
   $ cd python/training/classification
```
12. Set the NET and DATASET variables:
```
   $ NET=models/art_styles
   $ DATASET=data/art_styles
```
13. Run this command to see how it operates on an image from the academic folder:
```
   $ imagenet.py --model=$NET/resnet18.onnx --input_blob=input_0 --output_blob=output_0 --labels=$DATASET/labels.txt $DATASET/test/academic/232332.jpg academic.jpg
```
14. Open the new image in VSCode to see how the model works or scroll up to see how the model classified the image if you are using a regular terminal.
15. To run the model on a different image, change this section of the code: /academic/232332.jpg academic.jpg
16. The first 'academic' refers to which set of images in the test folder you are choosing from. '232332.jpg' is the image you are classifying in the set of images you chose. Finally, 'academic.jpg' is the name of the image that will be exported once the model finishes classifying it.



View a video explanation here: https://www.youtube.com/watch?v=7_8zBcVsZFo
