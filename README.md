# PicSum

## Introduction

Picsum generates abstractive and extractive summaries to enable them to digest voluminous information in shorter periods. It further enhances their comprehension 
by creating fill-in-the-blank questions from the summaries, enabling them to assess their understanding of the condensed information.

## Methodology

The project takes in an image as input. This image could be a picture of notes or a screenshot of a pdf. It processes the image and generates the summary of the given text. It also highlights all the important sentences in the image, thereby emphasizing on the important parts. It also creates a fill in the blanks for the user to exercise upon.

* Step-1 OCR: This involves reading text from the image. The image's text is read using Tesseract OCR (optical character recognition unit), which employs adaptive thresholding to preprocess the image. It then generates character outlines around the text. These outlines are organized into lines and words and matched against existing wordlists. If a match is found, the resulting word is output.

* Step-2 Generate Summary: Now, we will create a summary from the text,we employ a transformer model called BART. This approach consists of two stages: encoding and decoding. Encoding involves generating tokens from the extracted information, while decoding involves creating a summary from these tokens.

* Step-3 Getting Important Sentences: This step involves highlighting important sentences from the text. This is done by creating word embeddings in the form of vectors and then calculating the similarity between the sentences using cosine distance between a pair of vectors. Then we create a graph from the similarity matrix generated. This graph is page-ranked to find out the important sentences in the text.

* Step-4 Generate Fill-in-the-blanks: This involves generating fill in the blanks. Question-answer pairs are generated using the AAQG method with T5 (Answer Aware question generation), are converted into declarative sentences using the BART model trained on the QA2D dataset to generate fill-in-the-blank questions.

![Demo Picture 1](https://github.com/SahilDanayak/PicSum/blob/master/PicSum-Demo-Picture1.png?raw=true)
![Demo Picture 2](https://github.com/SahilDanayak/PicSum/blob/master/PicSum-Demo-Picture2.png?raw=true)

## Result

The output is given in 4 different texts depicting the result of ocr, the generated summary, the important sentences and the associated text. These texts can help the user to quickly navigate through and understand the crux of the part.
