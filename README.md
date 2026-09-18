# Enhanced Handwriting Digit Recognition

A polished, dark-themed desktop app that recognizes handwritten digits (0â€“9)
**live as you draw**, powered by a convolutional neural network trained on
MNIST. The enhanced version adds live prediction, canvas tooling, and rich
model-inspection views on top of the original GUI.

![Python](https://img.shields.io/badge/Python-3.x-3776AB)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-FF6F00)
![CNN](https://img.shields.io/badge/CNN-Keras-FF6F00)
![GUI](https://img.shields.io/badge/GUI-Tkinter-blue)

## Features

- **Live prediction** while you draw â€” no button presses needed
- Smooth brush engine with **S / M / L pen sizes**
- **Eraser**, **Undo**, and **Clear** tools
- Confidence shown with color coding (green / amber / red)
- **All-class probability bars** for every digit 0â€“9
- **"What the model sees"** preview showing the model's 28Ã—28 input
- **Test-set grid** and **confusion matrix** visualization (matplotlib)
- **Retrain** the model right from the app
- Auto-loads `digit_model.keras`; if missing, trains on MNIST in a background
  thread so the UI never freezes
- Dark, modern theme with a status bar and tooltips

## Getting Started

### Requirements

Install the dependencies:

```bash
pip install tensorflow matplotlib numpy
```

### Run the app

```bash
python Enhanced_Handwriting_Digit_Recognition/GUI_hand_writing_digit_recognition_app.py
```

**First launch:** if `digit_model.keras` is not present, the app automatically
downloads the MNIST dataset and trains the model (8 epochs) in the background.
Subsequent launches load the saved model instantly.

## Model architecture

A compact CNN, trained on MNIST (28Ã—28 grayscale digits):

```
Input (28Ã—28Ã—1)
  â†’ Conv2D 32 + ReLU â†’ MaxPool 2Ã—2 â†’ Dropout
  â†’ Conv2D 64 + ReLU â†’ MaxPool 2Ã—2 â†’ Dropout
  â†’ Flatten â†’ Dense 128 + ReLU â†’ Dropout
  â†’ Dense 10 + Softmax
```

Trained with the Adam optimizer and sparse categorical cross-entropy, with
early stopping and learning-rate reduction callbacks.

## Project structure

```
enhanced_handwriting_digit_recognition_app/
â””â”€â”€ Enhanced_Handwriting_Digit_Recognition/
    â”œâ”€â”€ GUI_hand_writing_digit_recognition_app.py   # App entry point
    â””â”€â”€ digit_model.keras                           # Trained model
```

## License

This project is open-source and available under the [MIT License](LICENSE).