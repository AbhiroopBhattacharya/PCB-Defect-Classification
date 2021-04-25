# PCB-Defect-Classification

Manual visual inspection of Printed Ciruit Boards involve a significant amount of cost and expertise. Researchers have used various methods for defect detection on a PCB board.
Earlier works focus on wavelet based algorithm which has lower computational cost. However, the method does not generalise to different type of defects. 
Recently, researchers have used image processing with deep neural networks to improve the generalization ability of the defect detection task. 
Researchers have explored the use of Convolutional Neural Networks for the automatic classification of defects. There are a number of challenges with the classification
of defects in Printed Circuit Boards. They are outlined below: 
1. Class Imbalance: There are a very few samples with defects as compared to boards without a defect. Also, certain types of defects like spurts or spurious copper may be
                    more prevalant in the training dataset. This class imbalance needs to handled by the machine learning framework.
2. Low Tolerance for False Negatives: The fabrication unit may incurr a significant financial, legal and reputational loss if a defected printed circuit board is 
                                      shipped for commercial use. Thus, the network should be able to correctly capture all defects in a circuit board. Also, 
                                      misclassification of defects may result in incorrect remedial measures which may lead to losses. 
3. Lack of training data: There are a few small public datasets which may be used to train the neural network. Convolutional Neural networks require large amounts
                          of training data. Transfer learning provides a viable alternative. This also enables the framework to leverage state of the art models for 
                          classification.
4. Computational requirement: Deep neural networks require significant computational resources to train the model and tune the hyperparameters. The author recommends users to use a GPU
                              to train the model.
                              
                              
This project uses the Deep PCB Dataset( https://github.com/tangsanli5201/DeepPCB.git) for training the models. A reference method has been used to classify the images.
The approach can be brodly classified into the following steps:
1. Image Binarization using Adaptive threshold
2. Align the template boards
3. Image Differencing 
4. Contour Extraction
5. Image Labelling 

The images have been labelled using the Defect Trucker app (https://github.com/sean-mcclure/defect_turker.git). OpenCV library has been used for the image processing 
steps and FastAI library has been used for training the convolutional neural networks. The Google Colaboratory GPU environment has been used to train the models.

The ResNet34, ResNet50, ResNet 101, VGG 16 and VGG19 models were used for the experiments. The models were trained using the fit one cycle approach. 
This method provides better results and requires less compute compared to annealing of learning rates. The learning rates of the model were fine tuned based 
on the data and we found that this improved the accuracy in most cases. The model was able to achieve a best performance with low test error (~11-12%). The model was able
to classify the following defect types with reasonable accuracy:
1. Spur
2. Spurious Copper
3. Short 
