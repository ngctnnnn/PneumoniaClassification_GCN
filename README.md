<div align='center'>
  
  ## Graph Convolutional Neural Network as an explainable Pneumonia classifier

  </div>

Pneumonia is a casual pathological condition and is categorized into many types with different etiologies. However, in order to examine and kill the illness proprly, there is an urgent need in identifying pneumonia infection and this is a highly specified work requiring a great deal of knowledge from specialized doctors. To identify the causes, to prevent pneumonia better, as well as save the human resources for hospitals, many researches did apply machine learning techniques on automatically classifying Chest X-ray images (CXR) to recognize whether the lungs are normal or pneumonia, whether the disease is viral pneumonia or bacteria pneumonia. In this work, we use Graph Convolutional Neural Networks (GCNs) as a CXR classifier and achieve the accuracy of <b> 96.75% </b> in Labeled Optical Coherence Tomography (OCT) and Chest X-Ray Images for Classification dataset.
 
<b> Keywords: </b> <i>Graph Convolutional Neural Networks (GCNs), Chest X-ray (CXR), Pneumonia, Classfication</i>

---

### Overall pipeline in this work

<div align='center'>

![pipeline](https://user-images.githubusercontent.com/67086934/173236571-7bb66ea5-8541-4f98-9bb0-bc11eb9c8de2.png)

</div>

#### 1. Preprocessing
- Original CXR images would be resized into 224x224 resolution.
- Edge detection on resized CXR images.

<div align='center'>

<img width="502" alt="Screen Shot 2022-06-12 at 21 04 22" src="https://user-images.githubusercontent.com/67086934/173237011-56cde48d-923b-4119-9c09-765391422af4.png">
  
</div>

#### 2. Graph Construction
- Pixels having grayscale intensity value of `128` is qualified as a node and feature of a node consists of the grayscale intensity of the corresponding pixels.
- Edge exists between 2 nodes representing neighboring pixels from original images.
- Node attributes, which are grayscale values, are normalized graph-wise.

#### 3. Architecture construction
- In this work, GCN convolutional layers are designed to exchange information toward each other the same as the mechanism in
message-passing neural network. 
- MPNN comprises of 2 primary steps: UPDATE and READOUT
  - <b> UPDATE: </b> Feature vectors h(v) of node v , ∀v ∈ V are sequentially updated via 2 minor phases: 
    - <i> Aggregation:</i> neighboring nodes features are synthesized into one feature vector  
    - <i> Update:</i> aggregated feature vector would be assigned to node v.      
  -> The update phase would be conducted for T iterations before moving to final step.
  - <b> READOUT: </b> The final graph is pooled via a Log-Softmax activation.
  
  <div> 
  
  <img width="492" alt="Screen Shot 2022-06-12 at 21 11 55" src="https://user-images.githubusercontent.com/67086934/173237357-f23ac6bb-fa8c-4ce9-af53-5f9e5bec5f88.png">

   </div>

#### 4. Dataset 
To validate the applied method, we use ”Labeled Optical Coherence Tomography (OCT) and Chest X-Ray Images for Classification dataset” with 6114 CXR images. 

<div align='center'>

<img width="321" alt="Screen Shot 2022-06-12 at 21 17 10" src="https://user-images.githubusercontent.com/67086934/173237585-97fc20bb-fc4c-45f2-a8b1-9c86924314c8.png">

</div>

#### 5. Result comparison

<div align='center'>
  
<img width="569" alt="Screen Shot 2022-06-12 at 21 20 58" src="https://user-images.githubusercontent.com/67086934/173237730-85dc571e-9210-4726-9790-f990378f1e08.png">

</div>

<div align='center'>
  
<img width="574" alt="Screen Shot 2022-06-12 at 21 21 31" src="https://user-images.githubusercontent.com/67086934/173237753-5575603d-cb96-40b5-9561-e49bb0ff4d9e.png">

</div>

#### 6. References
[1] Abien Fred Agarap. Deep learning using rectifiedinear units (relu). arXiv preprint arXiv:1803.08375, 2018.       

[2] John Canny. A computational approach to edge detection. IEEE Transactions on pattern analysis and machine intelligence, (6):679–698, 1986.    
   
[3] Alexandre de Brébisson and Pascal Vincent. An exploration of softmax alternatives belonging to the spherical loss family, 2015.     

[4] Justin Gilmer, Samuel S Schoenholz, Patrick F Riley, Oriol Vinyals, and George E Dahl. Message passing neural networks. In Machine learning meets quantum physics, pages 199–214. Springer, 2020.     

[5] Kaiming He, Xiangyu Zhang, Shaoqing Ren, and Jian Sun. Deep residual learning for image recognition, 2015.     

[6] Nick Kanopoulos, Nagesh Vasanthavada, and Robert L Baker. Design of an image edge detection filter using the sobel operator. IEEE Journal of solid-state circuits, 23(2):358–367, 1988.     

[7] Daniel Kermanym, Kang Zhang, and Michael Goldbaum. Labeled optical coherence tomography (oct) and chest x-ray images for classification. 2018.
[8] Diederik P. Kingma and Jimmy Ba. Adam: A method for stochastic optimization, 2014.     

[9] Cong Ma, Fan Yang, Yuan Li, Huizhu Jia, Xiaodong Xie, and Wen Gao. Deep human-interaction and association by graph-based learning for multiple object tracking in the wild. Int. J. Comput. Vision, 129(6):1993–2010, jun 2021.     

[10] Ramprasaath R. Selvaraju, Michael Cogswell, Abhishek Das, Ramakrishna Vedantam, Devi Parikh, and Dhruv Batra. Grad-CAM: Visual explanations from deep networks via gradient-based localization. International Journal of Computer Vision, 128(2):336–359, oct 2019.     

[11] Karen Simonyan and Andrew Zisserman. Very deep convolutional networks for large-scale image recognition, 2014.     

[12] An Vo and Tan Ngoc Pham. Detecting covid-19 and pneumonia with chest x-ray images using deep convolutional neural networks. Introduction to Computer Vision, June 2021.     

[13] Peng Xu, Chaitanya K. Joshi, and Xavier Bresson. Multi-graph transformer for free-hand sketch recognition, 2019.
