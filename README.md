# Smart Parking Occupancy Detection using IoT and CNN

This project finds whether a parking slot is free or occupied.

- An ESP32 with an HC-SR04 ultrasonic sensor (simulated on Wokwi) shows the status with red and green LEDs.
- A small CNN looks at a cropped image of one slot and says free or occupied.

## Results (validation set, 17,854 images)
- Keras model: 92.95 % accuracy, ROC-AUC 0.9846
- int8 TensorFlow Lite model: 93.28 % accuracy, 177.9 KB

## Dataset
CNRPark-EXT from Roboflow Universe (89,270 slot images, 41,720 free and 47,550 occupied).
The dataset is not in this repo. The notebook downloads it with your own Roboflow API key.

## Folders
- notebook: Google Colab notebook (download, crop, train, evaluate, convert)
- model: trained Keras model, TFLite models, C header for ESP32
- results: confusion matrix, ROC curve, training curves, demo images

## How to run
Open the notebook in Google Colab, replace PASTE_YOUR_KEY_HERE with your own Roboflow API key, and run the cells in order.

## Limitations
The validation split is random, there is no separate test set, free slots are mislabelled as occupied more often (11.2 %) than the reverse (3.4 %), and the model has not been run on an ESP32-CAM yet.
