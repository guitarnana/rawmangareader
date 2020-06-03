# Raw manga reader

## Setup

The project requires
- [detectron2](https://github.com/facebookresearch/detectron2)
- pytorch
- [pytesseract](https://github.com/madmaze/pytesseract)
- opencv
- pyQt5

You will need to install [tesseract](https://github.com/tesseract-ocr/tesseract) on your machine
and make sure that tesseract command is accessible by adding the installed directory to the path.

detectron2 is pre-built for windows 10 and CUDA 10.2. The whl file for this prebuilt package is under detectron2_win_cuda10.2 directory.

This command below will installed all the dependency including prebuilt detectron2.

`pip install -r requirements.txt`

For other platform or setup, you will need to compile your own detectron2.

## Getting Microsoft translator API subscription key

The program requires Microsoft translator API subscription key to run. You can sign up for free. It is free for under 2M char translated per month.
Make sure that the location is **Global** when you create a service.

https://docs.microsoft.com/en-us/azure/cognitive-services/translator/translator-how-to-signup


## Running the program

`python -m rawmangareader`

Once the program starts, you will need to open **File > Setting** to setup translator API subscription key.

Next you can do **File > Open** to open a directory containing images.

## How it works

I trained ML model using detectron2 to be able to detect basic manga speech box. Then I feed the output to OCR.
For this project I use [pytesseract](https://github.com/madmaze/pytesseract), which is an open source OCR tool for python based on [tesseract](https://github.com/tesseract-ocr/tesseract). After I got the text from OCR output, I use [Microsoft translator API](https://docs.microsoft.com/en-us/azure/cognitive-services/translator/translator-how-to-signup) to translate the text.

Changing between image might be a bit slow due to the program running ML algorithm to predict where the speech box will be.

You can modify the original text if the what the program detects is incorrect or contains weird character. Then you can click **Translate all text** button to do a translation again.