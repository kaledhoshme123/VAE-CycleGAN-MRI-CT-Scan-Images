# VAE-CycleGAN (MRI, CT Scan) Images:
- The study works on generating CT images from MRI images, where unsupervised learning was used using VAE-CycleGan.
Since the number of samples included in the data set used in the study, and therefore in this case we are in a state of epistemic uncertainty, therefore probabilistic models were used in forming the latent space.
- The current study is a continuation of the study ([Multi-Scale CycleGAN Night to Day](https://github.com/kaledhoshme123/Multi-Scale-CycleGAN-Night-to-Day)), but the difference between them is that in the study we were in the same field but working on generating the same scene at night or during the day, but the current study works on moving from one probability distribution to another probability distribution (i.e. studying the transition from one probability distribution to another probability distribution Another) and thus several properties included in the neural network were removed in the study ([Multi-Scale CycleGAN Night to Day](https://github.com/kaledhoshme123/Multi-Scale-CycleGAN-Night-to-Day)).
- The shaping of the latent space was adjusted by making the probability distributions of the latent space as close as possible to the standard Gaussian normal distribution.
The problem facing the research: What features does the discriminator look for to identify CT and MRI images? The same discriminator structure was used in the study ([Multi-Scale CycleGAN Night to Day](https://github.com/kaledhoshme123/Multi-Scale-CycleGAN-Night-to-Day)), but with the addition of a deeper discriminator structure (to extract more important features), and at the same time Time adjusts the features extracted from previous convolutional layers to fit the last convolutional layer in the discriminator structure.
- The derivative independence methodology used in the discriminator (which works to adjust the features that are extracted from the convolutional layers in the previous convolutional layers depending on the output of the last convolutional layer and at the same time examines the features extracted from the previous convolutional layers as real or fake (that is, the neural network in this The case is forced to adjust its weights in the previous convolutional layers so that they are real and not fake, and at the same time they must be appropriate to the output of the last convolutional layer - this helps the discriminator to have a deep understanding of the features that should be focused.
- By distinguishing between real and fake images, it helps in arriving at an accurate generating result.
- The study achieved good results when transitioning from MRI images to CT images, and acceptable results when transitioning from CT images to MRI images (the reason for this is the ease of transitioning from MRI images to CT images and its difficulty in the opposite direction. As well as the small number of samples included dataset).
- I trained the proposed model 50,000 Epochs using Google Colab.
- I used data augmentation to generate an additional copy of each sample that is passed over each time, in order to expand the generation capacity of the model due to the small number of samples included in the Dataset.
# Dataset Used:
https://www.kaggle.com/datasets/darren2020/ct-to-mri-cgan
# Results:
The model has been tested in generating a number of CT scan images from MRI images, and vice versa, and the results are shown in the samples that we showed.
| Results | #1    |
| :---:   | :---: |
| CT TO MRI |![download (23)](https://github.com/kaledhoshme123/VAE-CycleGAN-MRI-CT-Scan-Images/assets/108609519/06bd2425-245d-45ce-b11b-19d88ce1a01e)|
| MRI TO CT |![download (25)](https://github.com/kaledhoshme123/VAE-CycleGAN-MRI-CT-Scan-Images/assets/108609519/f51aae03-85c8-4f7f-8385-076cfa7f4448)|

# Test Generation:
- In order to use a more reliable methodology in evaluating the performance of the model that I trained, I used images that the model did not see during training, and for each image I did the following:
# The First Case:
- I have CT images that I converted into an MRI, then I recovered the CT image from the MRI images, and then I studied the difference between the basic CT images and the CT images that were retrieved from the MRI that was generated from the CT images.
- We note here that the loss is small for the CT images, and this indicates that the trained model was able to study the correspondence of the two probability distributions for each type.
# The second case:
- Moving from MRI images to CT images and then restoring the MRI from the CT images. Thus, we notice that the loss here is greater when comparing the original MRI images to the generated images, due to the small number of samples included in the dataset.

| Test Generation | #1    |
| :---:   | :---: |
| First Case | ![download (27)](https://github.com/kaledhoshme123/VAE-CycleGAN-MRI-CT-Scan-Images/assets/108609519/3a672b9b-088c-4c95-991b-68b7c437bc2c) |
| Second Case | ![download (28)](https://github.com/kaledhoshme123/VAE-CycleGAN-MRI-CT-Scan-Images/assets/108609519/7c4475f7-dc26-4d59-8473-3116f3f4ea92)|

# Conclusion
- This measure is considered acceptable for studying the success of the obstetrics process, but it is not a source of trust for me yet, because the number of samples is small, and therefore in this case the proposed model is forced to study the convergence between the two probability distributions (CT images and MRI images), and therefore in this case, given the lack of samples and the damage The model is to reduce the value of the loss in each epoch. Some cases may be incorrect during the projection process, but since the samples are small, the result is considered acceptable.
# Note: Please make sure that
tensorflow==2.15.0

tensorflow-probability==0.23.0
## You can download the required version through
!pip install tensorflow==2.15.0

!pip install tensorflow-probability==0.23.0

for the code to work.
