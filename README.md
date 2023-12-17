# graduation_project
### MAINTAINING CLEAR VISION FOR AUTONOMOUS CARS

image dehazing is a vital task in computer vision that has garnered significant attention in recent years. The development of various prior-based, deep learning-based, and frequency domain learning approaches has shown promise in homogeneous dehazing tasks, but their performance is limited in non-homogeneous dehazing. The recent advancements in the Vision Transformer models suggest that future research may lead to more efficient and effective image dehazing techniques.


#### Methodology:
The proposed image restoration network uses a two-branch encoder architecture with different operations to restore hazy images, including the DWT transform, NAFNet, and Restormer's Transformer block. The network captures both low-level and high-level image features, resulting in high-quality restorations of hazy images. By using distinct information from each branch and proper fusion strategies, the performance of image dehazing is greatly boosted.


### Data flow in overall arch:
J => hazy image inputted to two branch encoders which have separate data paths. The first branch is the DWT (De Haar) transformation which applies a combination of 2 filters (LPF -> LPF, LPF -> HPF, HPF-> LPF,  HPF -> HPF) to the image to extract the 4 low and high frequency components. Each DWT encoder level undergoes downsampling then a NAFBlock for additional feature extraction.  The second branch has the input downsampled and processed by the restormer transformer block, then this output is concatenated with the corresponding low frequency feature maps from the first branch.The output of the downsampling is then fed to the resnet bottleneck block to provide a skip connection to the corresponding decoder level. After 5 downsampling stages, the output gets upsampled then passes through 4 decoder stages. Each decoder stages concatenates its input with the corresponding high frequency component then feeds it to the Selective Residual Block (SRB). The output of SRB is concatenated with the skip connection from the corresponding resnet bottleneck and fed to the restormer refinement block. Finally, the output is upsampled, and the cycle continuess

this is the drive folder for the datasets and the checkpoints to save: https://drive.google.com/drive/folders/1-wGONRRgjuZTtHoivJx1dgRmJyokF5gb?usp=sharing
