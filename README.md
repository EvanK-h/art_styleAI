# art_styleAI

This model classifies an image of Academic Art, Japanese Art, or Western Medieval Art into one of these three classes. This model can be especially useful for art students trying to classify artworks and find their art style, or for people who are just getting into art and want to know what art style a painting was made in.

## The Algorithm

This model is a re-trained ResNet-18 model which was created on a Jetson Nano and trained on a dataset of Academic Art, Japanese Art, or Western Medieval Art. It runs on an imagenet.py program that will classify a piece of artowork as one of these three art styles.

## Running this project

1. Make sure that both the Jetson Inference library and Python3 are installed on your Jetson Nano.
2. Download the resnet18.onnx and model_best.pth.tar. Links to the models:

[View a video explanation here](video link)
