# my_fid-clean-fid
PyTorch - FID calculation with proper image resizing and quantization steps [CVPR 2022]
                                 Fréchet Inception Distance
<div align=center><img src="https://user-images.githubusercontent.com/33627638/168471544-a74736a6-ed87-4d44-bd45-a4a9f9c31ea3.png" width="300" height="500" /></div>
<p align="center">ImageNet-C bright</p>
- The FID score will increase if the bright increase. FID(from up to bottom): 172, 175, 180, 188, 197 (100 images-100 images with different bright)


-  Although FID needs at least 10,000 images, we compare with the same images with different bright. 


- Unlike supervised learning, there is expected image for GAN. And discriminator is overfitting to dataset.


- So we need to find a metric to evaluate the generated images. Fidelity and diversity are two indicators of evaluation.


- We could use the feature extractor to extract features from the images and compare them with dataset.


- The pre-trained classifier trained on the huge dataset ImageNet can be used as the feature extractor.

- We will get the embeddings or feature vectors extracted from the generated images and dataset.

- We could select Inception-v3 model as the training model.

- It's wider with 1X1, 3X3, 5X5, filters operating on the same level, 42 layers deep, and input 299X299X3 with the output vector of size 2048.

- We could use these 2048 dimensional feature vectors to calculate feature distance.

- Fréchet distance: The Fréchet distance between the two curves is the length of the shortest leash sufficient for both to traverse their separate paths from start to finish. Or the minimized maximum leash between two point sets from start to end.
<div align=center><img src="https://user-images.githubusercontent.com/33627638/168473048-3dd2737e-776d-4e04-9d95-fd25bf877ef5.png" width="500" height="300" /></div>
<div align=center><img src="https://user-images.githubusercontent.com/33627638/168473022-bda49231-f91b-4b87-b3c0-10d25ce8cce9.png" width="500" height="300" /></div>
<div align=center><img src="https://user-images.githubusercontent.com/33627638/168473031-1cdd9d0e-0c57-4403-8a55-1e8b89765f99.png" width="500" height="300" /></div>
<div align=center><img src="https://user-images.githubusercontent.com/33627638/168473035-41c96e04-556c-4257-9a88-5aff3740f647.png" width="500" height="300" /></div>

- Generated images and images in dataset are considered to correspond to multivariate normal distributions.
- Shortcomings:


  - Since ImageNet is mainly composed of dogs, cats, etc., maybe it’s not good for handwritten digits.The pre-trained Inception model may not capture all features. 


  - Needs a large sample size


  - Slow to run, only mean and covariance are used (limited statistics)


 - 10,000 is the suggested minimum sample size to calculate FID.
 


