
code is available at https://colab.research.google.com/drive/1-y2STlBa0v4GE8Eep1jGf-zxIimQ0-Sp#scrollTo=MCA7ed62GxtV

**Technical & Code Contributions:**

**Model Development & Customization:**  
• Implemented and adapted the `inception_net_norm` architecture for 3D video data.  
• Designed and implemented custom modules like `my_Conv3d` and `inception_block_norm`.  
• Modified the network for specific deepfake types (e.g., handling or excluding "NeuralTextures").  
• Optimized model performance through hyperparameter tuning and regularization (e.g., dropout).

**Data Preprocessing Pipelines:**  
• Developed or optimized face extraction from videos (e.g., `og_video_to_face`, `fake_video_to_face`).  
• Managed bounding box data and CSV-based metadata integration.

**Training & Evaluation Framework:**  
• Built PyTorch training loop with loss functions, optimizers, and schedulers.  
• Implemented metrics (accuracy, precision, recall, F1-score) and confusion matrices.  
• Handled training logistics, including checkpointing.

**Research & Analytical Contributions:**

**Comparative Analysis:**  
• Analyzed model performance across deepfake types (e.g., “NeuralTextures”).  
• Interpreted architectural and training impacts on detection accuracy.

**Dataset Understanding:**  
• Evaluated dataset characteristics (e.g., deepfake type distribution, face quality).  
• Identified biases and challenges within the dataset.

Model Architechture:
![Model](https://github.com/Srabontideb/Deepfake_project/blob/863cc59cf9ad38e02764b3dff62c14d7a3b082fe/InceptionNet.png)

