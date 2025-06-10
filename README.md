Model Architechture:
![Model](https://github.com/Srabontideb/Deepfake_project/blob/863cc59cf9ad38e02764b3dff62c14d7a3b082fe/InceptionNet.png)
code is available at https://colab.research.google.com/drive/1-y2STlBa0v4GE8Eep1jGf-zxIimQ0-Sp#scrollTo=MCA7ed62GxtV

Technical & Code Contributions:

Model Development & Customization: 
•	Implementing and adapting the inception_net_norm architecture for 3D video data.
•	Designing and implementing custom modules like my_Conv3d and inception_block_norm.
•	Modifying the network for specific deepfake types (e.g., handling or excluding "NeuralTextures").
•	Optimizing model performance (e.g., through hyperparameter tuning, regularization techniques like dropout).
Data Preprocessing Pipelines: 
•	Developing or optimizing the face extraction process from videos (e.g., og_video_to_face, fake_video_to_face).
•	Implementing robust data loading and augmentation strategies for the deepfake dataset.
•	Managing and integrating bounding box information from CSV files.
Training & Evaluation Framework: 
•	Setting up the PyTorch training loop, including loss functions, optimizers, and schedulers.
•	Implementing evaluation metrics (accuracy, precision, recall, F1-score, confusion matrices) to assess model performance.
•	Handling training logistics such as saving/loading model checkpoints.

Research & Analytical Contributions:
Comparative Analysis: 
•	Analyzing the performance differences between models trained with and without specific deepfake types (e.g., "NeuralTextures").
•	Interpreting the impact of different architectural choices or training strategies on detection accuracy.
Dataset Understanding: 
•	Analyzing the characteristics of the deepfake datasets used (e.g., distribution of deepfake types, quality of extracted faces).
•	Identifying challenges or biases within the dataset.
