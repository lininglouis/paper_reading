## Notes on RCNN


#### training 

0) fined and get N class CNN classifier

pretrained CNN model on ImageNet
fine tune to N classes CNN net


1) generate proposals
warp prposal region into 227 x 227


2) large CNN extracting fixed-length features from regions

    a) use cnn, 
    b) take each proposal region image as input, 
    c) generate 4096 features for each region


3) class-specific SVM classifiers
N class SVM scores give scores for each proposal region


4) Bounding box regression to improve localization

    * use class-specific BB regressor for each detected image, given CNN features

    * learns to map a proposed box to GT box




#### predicting
for each image

    generate 2000 proposals
    
    generate 4096 feature for each proposal region
        
    together feature matrix 2000 x 4096 for each matrix  
    
    [ 2000 x 4096 ] [ 4096 x N classes] = [ 2000 x N classes ]
    
    use mutiple SVM classifiers to classify this 4096 features
    
    NMS: remove boxes close to highers scored region




评价
RCNN mainly plays as a **classifier**.
It does not predict object bounds(SS does this), except for refining it by bounding box regresion







