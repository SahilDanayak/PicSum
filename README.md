# PicSum

Try out the deployed model here : https://huggingface.co/spaces/SMD00/Image_Summarizer

## Introduction

Picsum generates abstractive and extractive summaries to enable them to digest voluminous information in shorter periods. It gives out the important sentences and further enhances their comprehension by answering their questions, enabling them to assess their understanding of the condensed information.

## Methodology

The project takes in an image as input. This image could be a picture of notes or a screenshot of a pdf. It processes the image and generates the summary of the given text. It also highlights all the important sentences in the image, thereby emphasizing on the important parts. It also answers questions related to the context.

* Step-1 OCR: This involves reading text from the image. The image's text is read using Tesseract OCR (optical character recognition unit), which employs adaptive thresholding to preprocess the image. It then generates character outlines around the text. These outlines are organized into lines and words and matched against existing wordlists. If a match is found, the resulting word is output.

* Step-2 Generate Summary: Now, we will create a summary from the text,we employ a transformer model called BART. This approach consists of two stages: encoding and decoding. Encoding involves generating tokens from the extracted information, while decoding involves creating a summary from these tokens.

* Step-3 Getting Important Sentences: This step involves highlighting important sentences from the text. This is done by creating word embeddings in the form of vectors and then calculating the similarity between the sentences using cosine distance between a pair of vectors. Then we create a graph from the similarity matrix generated. This graph is page-ranked to find out the important sentences in the text.

* Step-4 Question and Answers: TThis involves generating Answers of user input questions. Question-answer pairs are generated using by fine tuning DistilBERT and Roberta model on the squad dataset using 5000 question answer tuples. 

Some of the results: 

<img src="https://github.com/SahilDanayak/PicSum/blob/main/PicSum-Demo-Picture1.png?raw=true" width="600" alt="Demo Picture 1">
<img src="https://github.com/SahilDanayak/PicSum/blob/main/PicSum-Demo-Picture2.png?raw=true" width="600" alt="Demo Picture 2">

## Result

The output gives 3 different texts depicting the the generated summary, the important sentences and the answers of the given questions. These texts can help the user to quickly navigate through and understand the crux of the part.
