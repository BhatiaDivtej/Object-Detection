**  Object Detection: MaskRCNN in Pytorch **
    1 Problem Definition: Object Detection
RGB ImageàBoundary Boxes of different object (cars, pedestrians and so on) COMP3340 Applied Deep Learning
     2

    1 Problem Definition: Applications
   Robotic Manipulation Autonomous Driving
 COMP3340 Applied Deep Learning
 3

    2 Classification and Object detection
   COMP3340 Applied Deep Learning
 4

    3
Faster RCNN: Overview
Input image
Conv Conv
COMP3340 Applied Deep Learning
ConvNet
feature map
feature map
         proposal
         
    3
Input image
[ H , W , 3 ]
H, W: height and width of the original image
3: R, G, B channels
Faster RCNN: Backbone
       Conv feature map
[ 𝐻! , 𝑊! , C ]
𝐻! , 𝑊! : height and width of
feature map
C: the number of feature channels
ResNet or VggNet as the backbone network to extract feature map.
 ConvNet
 COMP3340 Applied Deep Learning
 
    3
Faster RCNN: RoI Pooling
  Region of Interest: [5,7] Pooled shape: [2,2]
 COMP3340 Applied Deep Learning
 
    3
Faster RCNN: Region Proposal Network
Conv feature map
[ 𝐻! , 𝑊! , C ]
COMP3340 Applied Deep Learning
Conv feature map
1 Generate boundary boxes at each pixel. K * 𝐻! * 𝑊! boxes 2 RoI pooling
3 Pass through convolutional and linear layer to achieve
`objectness score` and `box refinement`
4 Select top boxes according to `objectness score`.
       proposal
    
    3
Faster RCNN: Region Proposal Network
    COMP3340 Applied Deep Learning [1] Shaoqin Ren, et al, Faster R-CNN: Towards Real-Time Object Detection with Region Proposal Networks, NeurIPS2015. [2] These figures are borrowed from CS231n
 
    3
Faster RCNN: Box classification and Refinement
           proposal
     ConvNet
Conv feature map
Conv feature map
    Input image
COMP3340 Applied Deep Learning [1] Shaoqin Ren, et al, Faster R-CNN: Towards Real-Time Object Detection with Region Proposal Networks, NeurIPS2015. [2] Image captions are inspired from CS231n
  
    4
RoI Align
   COMP3340 Applied Deep Learning
 
    4
RoI Align vs RoI Pooling
   Reduce the Error brought by quantitation
 COMP3340 Applied Deep Learning
 
    5
Fully Convolutional Network for instance segmentation
   A Unified Framework for detection, segmentation and instance segmentation
 COMP3340 Applied Deep Learning
 
    6
Once the detector outputs a large number of bounding boxes, it is necessary to filter out the best ones. NMS is the most commonly used algorithm for this task. Typically, NMS filters proposals according to the IOU between the bounding boxes.
NMS
    COMP3340 Applied Deep Learning
 
    6
NMS
   COMP3340 Applied Deep Learning
 
    7
Loss Function
  Classification loss and Box regression loss: the same as that in Faster RCNN Mask loss: Binary Cross entropy loss with 0àno instance and 1àinstance.
 COMP3340 Applied Deep Learning
 
    8
Evaluation Metrics
Positive: the network predicts that the box contains an object.
Precision: Measure the percentage that the predictions are correct.
Recall: Measure the percentage that the network successfully predict the ground truth.
   COMP3340 Applied Deep Learning
 
    8
Evaluation Metrics: Average Precision
Rank according to the score
Plot the Precision-Recall curve
    AP=(5×1.0+4×0.57+2×0.5)/11=0.75
 COMP3340 Applied Deep Learning
 
    8
Implementation in Pytorch
  COMP3340 Applied Deep Learning
 
