### GAN Kaggle Competition

#### Problem Description
Build and train a GAN on the included Monet dataset to generate images in the style of Monet.  The zip file submission containing 7000 to 10000 Monet-like jpegs will be evaluated on MiFID (Memorization-informed Fréchet Inception Distance) metric.

#### Data Description
There are four directories in the dataset for this project.  Two monet directories containing the same 300 photos just in different data formats, namely TFRecord and jpeg.  Similarly, the two photo directories contain a variety of 7028 generic photos.  All photos, regardless of format are **RGB** of size **256 x 256**.  Those photos in the monet directory are to be used to train the model, and the photos directory can be used to add monet-style to generate fake Monets...Monauxs :)

#### Analysis
In reading the optional reading for the week, I can across a very similar task as Monaux.  Jonathon Hui did a great job of breaking down the exercise using CycleGAN:

>The concept of applying GAN to an existing design is very simple. We can treat the original problem as a simple image reconstruction. We use a deep network G to convert image x to y. We reverse the process with another deep network F to reconstruct the image. Then, we use a mean square error MSE to guide the training of G and F.
>
>![CycleGAN1.jpg](attachment:70bdb454-7bc0-42ba-83dc-a13df1370cee.jpg)
>
>However, we are not interested in reconstructing images. We want to create y resembling certain styles. In GAN, a discriminator D is added to an existing design to guide the generator network to perform better. D acts as a critic between the training samples and the generated images. Through this criticism, we use backpropagation to modify the generator to produce images that address the shortcoming identified by the discriminator. In this problem, we introduce a discriminator D to make sure Y resemble Van Gogh paintings.
>
>![CycleGAN2.png](attachment:c280810c-c573-4d98-bf65-0e9539918bac.png)
>
https://jonathan-hui.medium.com/gan-cyclegan-6a50e7600d7

CycleGAN transfers pictures from one domain (photo dataset) to another (Monet dataset). The implementation will include:

Generator: Uses a U-Net-inspired ResNet architecture.
Discriminator: A PatchGAN-based classifier.
CycleGAN Losses: Adversarial loss, cycle consistency loss, and identity loss.
