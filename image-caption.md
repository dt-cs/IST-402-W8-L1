
# Image Caption Generator Assignment Report

### Group 10 – Deebak, Andreea, Tsehynesh

---

## Overview

This assignment involved running a pre-built Python/Streamlit application inside Google Colab to implement an Image Caption Generator using the BLIP (Bootstrapping Language-Image Pre-training) model. The purpose was to explore how image captioning works, understand model integration within a Streamlit UI, and evaluate the accuracy and relevance of the generated captions.

---

## Code Analysis

The provided code builds a functional image-captioning web application using open-source libraries. It demonstrates key concepts such as model loading, UI creation, and web exposure via ngrok.

### 1. Environment Setup

The environment is prepared by cleaning previous background processes and installing required libraries. Tools such as Streamlit, Transformers, PIL, and Pyngrok are used for:

- building the user interface  
- loading and running the BLIP model  
- handling and processing images  
- exposing the Streamlit app to a public URL  

Ngrok is authenticated and used to create a public tunnel to the Streamlit app running on port 8501.

### 2. Model Loading

Inside the Streamlit application, the BLIP model components (the processor and the caption generation model) are loaded using the Salesforce BLIP image captioning base model. These components work together to convert the uploaded image into embeddings and then generate natural-language captions.

### 3. Application Execution

The user interface is structured to:

- allow the user to upload an image  
- preview the uploaded image  
- automatically run the caption-generation model  
- display the resulting caption  

| Component | Role in Code | Model Used |
|----------|--------------|------------|
| User Interface | Accepts images and displays output | Streamlit |
| Image Processing | Converts image for model input | PIL |
| Caption Generation | Produces the text description | BLIP (Salesforce Base) |

---

## Experiment

To evaluate the BLIP model’s performance, several images were uploaded through the Streamlit interface. The objective was to observe how accurately the generated captions matched the objects, actions, and environment within the images.

### 1. Example Caption: Indoor Object Scene

| Image | Caption Output |
|:---:|:---|
| ![](INSERT_IMAGE_URL_HERE) | “a desk with a laptop and a cup of coffee on it” |

**Analysis:**  
The caption accurately identifies the central objects and scene context. While the main elements are captured correctly, the model tends to omit finer details such as small desk accessories or environmental lighting.

---

### 2. Example Caption: Outdoor Landscape

| Image | Caption Output |
|:---:|:---|
| ![](INSERT_IMAGE_URL_HERE) | “a mountain range with a lake in front of it” |

**Analysis:**  
BLIP successfully identifies major landscape features. However, elements such as time of day, sky details, or vegetation type may not always be included, showing that the model prioritizes large-scale features over subtle details.

---

### 3. Example Caption: Animals

| Image | Caption Output |
|:---:|:---|
| ![](INSERT_IMAGE_URL_HERE) | “a dog running through a grassy field” |

**Analysis:**  
The model performs well with animal images, correctly describing both the subject and its action. BLIP demonstrates strong performance when the scene has a clear primary subject and simple background.

---

## Learnings

BLIP is effective at generating coherent and relevant captions for images, especially when:

- the main subject is prominent  
- the environment is simple or easily identifiable  
- the action is clear  

However, BLIP may miss:

- fine-grained visual details  
- textual elements within the image  
- complex interactions  
- subtle artistic styles  

The integration of BLIP with Streamlit and Ngrok provides a practical way to deploy real-time computer vision applications through a web browser. This assignment strengthened our understanding of building interactive AI tools using Streamlit and Hugging Face.

These insights will be applied to our final project, where we will use Streamlit to develop the user interface of our meeting summarizer application, including features for URL input, sending email summaries, and adding events to the calendar.
