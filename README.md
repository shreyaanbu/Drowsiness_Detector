# 1. Project Description  
This project focuses on developing a real-time driver drowsiness detection system using Artificial Intelligence and embedded hardware. The system uses a webcam to capture facial images of the user and processes them using a machine learning model trained on the Edge Impulse platform.  
The trained model is deployed on the Arduino UnoQ board, enabling on-device inference. The system continuously analyses eyes and facial patterns to determine whether the user is awake, drowsy, or in an unknown state. When drowsiness is detected, the system alerts the user through visual feedback, helping to prevent accidents caused by fatigue.  
By combining AI with low-power embedded hardware, this project demonstrates how intelligent monitoring systems can be implemented in real-world safety applications.  
  
# 2. Hardware Lineup  
The following hardware components were used to implement the drowsiness detection system:  
## 🔹 Processing & Control Unit  
Arduino UnoQ Board- Acts as the main embedded controller and runs the trained AI model locally for real-time inference.  
## 🔹 Development & Monitoring Device  
Laptop / PC-  
Training the model on Edge Impulse  
Uploading firmware to the board  
Monitoring output through the Serial Monitor  
Debugging and testing  
## 🔹 Vision Input  
Webcam- Captures real-time facial images of the user. These images are converted into grayscale format and used as input for the AI model  
## 🔹 Connectivity Devices  
USB Dongle- Enables wireless connectivity or additional communication support (if required).  
USB Type-A to Type-C Cable-  Used to connect the Arduino UnoQ board to the laptop for programming, power supply, and data transfer.  
## 🔹 Power Supply  
Power Adapter-  Provides stable external power to the system during standalone operation.  
  
# 3. User Interface & Feedback  
The drowsiness detection system provides user interaction and feedback through both software-based and visual interfaces, ensuring real-time monitoring and alerts.  
## 🔹 Edge Impulse Web Dashboard (Development Interface)  
During the development phase, the Edge Impulse web dashboard was used for:  
Uploading and managing training data  
Creating and configuring the impulse  
Training and validating the AI model  
Analysing model performance metrics  
Testing the model before deployment  
This interface helped in optimising the model for embedded deployment.  
## 🔹 Laptop Interface (Monitoring & Debugging)  
The laptop acts as the primary monitoring device during operation.  
Displays real-time classification results such as:  
Awake  
Drowsy  
Unknown  
Shows confidence scores for each prediction  
Live Webcam Preview  
Allows developers to verify proper face alignment and image capture  
Ensures consistent input quality for the AI model  
## 🔹 Visual Feedback System  
The system provides simple and effective visual feedback to the user.  
On-Screen Alerts (via Laptop)  
Text-based alerts displayed on the Web UI we developed  
Warning messages when drowsiness is detected  
Status Indication  
Normal State: “Awake” message displayed  
Warning State: “Drowsy” message displayed  
Error State: “Unknown” message displayed  
## 🔹 User Interaction Flow  
The webcam captures the user’s face.  
Images are processed by the AI model on the Arduino UnoQ board.  
Classification results are sent to the laptop.  
The results are displayed in the Web UI we developed.  
The user receives immediate feedback in case of drowsiness.  
This interface design ensures low complexity, fast response, and ease of use, making the system suitable for real-time safety applications.  
  
# 4. The AI Model  
The drowsiness detection system uses a Convolutional Neural Network (CNN) trained and deployed using the Edge Impulse platform. The model is designed for embedded machine learning, enabling real-time image classification directly on the Arduino UnoQ board without relying on cloud services.  
## 🔹 Model Development Platform  
Edge Impulse Studio  
Used for data management, preprocessing, model training, and deployment  
Optimized the model for low-power embedded devices  
Generated firmware compatible with the Arduino UnoQ board  
## 🔹 Dataset and Input Format  
Total images: 1860  
Training-testing split: 80% training, 20% testing  
Image type: Grayscale  
Image resolution: 96 × 96 pixels  
Input features: 9216   
Classes: Awake , Drowsy, Unknown  
Each input image is converted into grayscale and resized before being passed to the neural network.  
## 🔹 Model Architecture  
The AI model is based on a CNN architecture consisting of:  
Input Layer: 9216 features  
Convolution Layer 1: 16 filters, 3×3 kernel  
Convolution Layer 2: 32 filters, 3×3 kernel  
Flatten Layer  
Dropout Layer (0.25)  
Fully Connected Output Layer (3 classes)  
This structure allows the model to extract important facial features such as eye closure and facial posture while maintaining low memory usage.  
## 🔹 Model Optimisation  
To improve on-device performance on the Arduino UnoQ, the model was optimised using the Edge Impulse deployment tools.  
The model was deployed in Quantised (INT8) format, which converts floating-point values into 8-bit integers.  
INT8 Quantization  
Reduces model size  
Improves inference speed  
Lowers memory and power consumption  
Enables real-time execution on embedded hardware  
This optimisation allows efficient inference while maintaining high accuracy.  
## 🔹 On-Device (Edge) Processing  
A key feature of this system is local data processing on the board, also known as edge computing.  
All image processing and classification occur on the Arduino UnoQ  
No data is sent to external servers  
User privacy is maintained  
Low latency is achieved  
This makes the system reliable and suitable for real-time safety applications.  
## 🔹 Model Performance  
The trained model achieved high accuracy and reliability during testing:  
Overall Accuracy: 98.98%  
ROC-AUC Score: 0.9997  
Low Classification Loss  
The confusion matrix and classification report show strong performance across all classes, indicating effective discrimination between awake and drowsy states.  
These results demonstrate that the model is well-suited for real-time drowsiness detection.  
  
# 5. Software Architecture  
The software architecture of the drowsiness detection system follows a modular client–server style design. The system consists of three main layers: the Edge Impulse AI model, the backend controller, and the web-based user interface.  
## 🔹 Main Software Components  
## a. Edge Impulse AI Model Component  
This component handles both data preprocessing and inference.Integrated using the Edge Impulse deployment package.Model configuration defined in the YAML file.   
Performs internal preprocessing such as: Image resizing, Grayscale conversion, Normalization, Executes INT8 quantized inference, Produces classification probabilities   
This component works as a self-contained AI module that directly converts raw camera input into prediction results.  

## b. Backend Control Module (main.py)  
The main.py file acts as the core backend of the system.  
Loads and links the Edge Impulse model  
Manages camera input  
Sends frames to the AI model  
Receives inference results  
Implements application logic  
Connects the AI model with the Web UI  
It functions as the central controller that coordinates all software operations.  
  
## c. Web User Interface Module  
The user interface is implemented as a web-based dashboard using:  
index.html – Defines the structure of the web page  
styles.css – Handles visual styling and layout    
App.js – Implements dynamic behavior and interaction  
Functions of the Web UI include:   
Displaying live system status  
Showing prediction results  
Presenting confidence scores  
Providing visual alerts for drowsiness  
Allowing user interaction  
This interface enables easy monitoring through a browser without additional software.  
## 🔹 Configuration and Model Management (YAML File)  
The YAML configuration file defines the AI model and system parameters.  
Specifies model paths and metadata  
Defines input dimensions and formats    
Controls preprocessing settings  
Manages deployment parameters  
This file ensures consistent integration between the backend and the AI model.  


