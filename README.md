# Plant Disease Detection Using Deep Learning

**1st Year B.Tech CSE Project**

---

## Project Objective

The main objective of this project is to build a simple Deep Learning model that can detect diseases in plant leaves from images. This can help farmers identify plant diseases early and take necessary action.

---

## Introduction

Agriculture is the backbone of many countries. Plant diseases can reduce crop yield significantly. Traditional methods of detecting plant diseases require expert knowledge and are time-consuming.

In this project, we use **Deep Learning** (specifically a Convolutional Neural Network called ResNet-18) to automatically detect plant diseases from leaf images.

---

## Technologies Used

| Technology       | Purpose                          |
|------------------|----------------------------------|
| Python           | Programming language             |
| PyTorch          | Deep Learning framework          |
| torchvision      | Pretrained models & image tools  |
| ResNet-18        | CNN architecture                 |
| Gradio           | Simple web interface             |
| Pillow (PIL)     | Image processing                 |

---

## Dataset Information

We use the **PlantVillage** dataset.

- Contains thousands of images of healthy and diseased plant leaves
- Images are organized in folders (one folder per disease/class)
- Common crops: Tomato, Potato, Apple, Corn, Grape, etc.
- Example classes: `Tomato___Late_blight`, `Apple___healthy`, `Potato___Early_blight`

**Dataset structure expected:**

```
data/PlantVillage/
├── Apple___Apple_scab/
│   ├── image1.jpg
│   ├── image2.jpg
│   └── ...
├── Apple___healthy/
│   └── ...
├── Tomato___Late_blight/
│   └── ...
└── ...
```

---

## Project Folder Structure

```
Plant_Disease_Detection/
│
├── .gitignore
├── README.md
├── requirements.txt
├── train.py              ← Training script
├── predict.py            ← Prediction script
├── app.py                ← Gradio web app
│
├── data/
│   └── PlantVillage/     ← Put your dataset here
│
└── models/               ← Trained model will be saved here
```

---

## How the Model Works

1. **Input**: A leaf image (224 × 224 pixels)
2. **Feature Extraction**: ResNet-18 extracts important features from the image
3. **Classification**: The final layer predicts which disease the leaf has
4. **Output**: Disease name + confidence percentage

We use a **pretrained** ResNet-18 (trained on ImageNet) and only change the last layer to match the number of plant disease classes. This technique is called **Transfer Learning**.

---

## Installation Steps

1. Open terminal / VS Code terminal in the project folder.

2. (Optional but recommended) Create a virtual environment:
```bash
python -m venv venv
```

3. Activate the virtual environment:
   - Windows:
```bash
venv\Scripts\activate
```
   - Linux / Mac:
```bash
source venv/bin/activate
```

4. Install required packages:
```bash
pip install -r requirements.txt
```

---

## How to Train the Model

1. Make sure the PlantVillage dataset is inside `data/PlantVillage/`

2. Run the training command:
```bash
python train.py
```

3. The program will:
   - Load the images
   - Split them into training (80%) and validation (20%)
   - Train ResNet-18 for 5 epochs
   - Print loss and accuracy after every epoch
   - Save the best model in `models/plant_disease_model.pth`

**Example output during training:**
```
Using device: cpu
Loading dataset from: data/PlantVillage
Number of classes found: 15
Total images: 3000
Training images  : 2400
Validation images: 600

Starting training...

Epoch [1/5]
  Train Loss: 1.2345 | Train Acc: 65.20%
  Val Acc  : 72.50%
  --> Best model saved! (Val Acc: 72.50%)
...
```

---

## How to Predict an Image

After training is complete, you can test a single image:

```bash
python predict.py path/to/your_leaf.jpg
```

**Example:**
```bash
python predict.py test_leaf.jpg
```

**Example output:**
```
==================================================
       PLANT DISEASE PREDICTION RESULT
==================================================
Image          : test_leaf.jpg
Predicted Class: Tomato___Late_blight
Confidence     : 91.35%
==================================================
```

---

## How to Run the Gradio Web App

1. Make sure the model is already trained (`models/plant_disease_model.pth` exists).

2. Run:
```bash
python app.py
```

3. Open the link shown in the terminal (usually `http://127.0.0.1:7860`) in your browser.

4. Upload a leaf image and click Submit to see the prediction.

---

## Advantages

- Easy to use (just upload an image)
- Can detect multiple plant diseases
- Uses Transfer Learning → good results even with limited data
- Works on both CPU and GPU
- Simple web interface using Gradio

---

## Limitations

- Accuracy depends on the quality and quantity of training images
- May not work well on images taken in very different lighting conditions
- Only works for the classes present in the training dataset
- Requires the model to be trained first before prediction

---

## Future Scope

- Add more plant species and diseases
- Improve accuracy by training for more epochs
- Deploy the model as a mobile application
- Add treatment suggestions based on the predicted disease
- Collect real field images to make the model more robust

---

## Conclusion

This project successfully demonstrates how Deep Learning can be used to detect plant diseases from leaf images. Using a simple ResNet-18 model and Transfer Learning, we can build a useful tool that can help in early disease detection. The project is suitable for understanding the basics of CNN, Transfer Learning, and building a simple AI application.

---

**Developed as a 1st Year B.Tech CSE Academic Project**
