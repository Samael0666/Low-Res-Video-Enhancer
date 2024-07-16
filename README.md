
This repo here will enhance any low-resolution video. 

We will work this with CONDA.

Getting started

Install ANACONDA in your PC.
Open Anaconda Navigator and select Commad prompt.

Clone the repository for the enhancing model setup
Run 
    git clone https:/github.com/xinntao/Real-ESRGAN.git
    
Step 1: Creating a new Conda Environment
      
      conda create -n new python=3.8
Step 2: Activating Conda Environment
      
      conda activate new
Step 3: Installing cuda 11.3 

      conda install pytorch==1.12.1 torchvision==0.13.1 torchaudio==0.12.1 cudatoolkit=11.3 -c pytorch

Step 4: Installing required libraries

        pip install basicsr
        pip install tqdm
        pip install facexlib
        pip install gfpgan
        pip install opencv-python==1.24.0
        pip install numpy
        pip install pillow

Step 5: Develop the setup

      python setup.py develop

Step 6: Download the model and save it in experiments/pretrained_models in your project directory

      wget https://github.com/xinntao/Real-ESRGAN/releases/download/v0.1.0/RealESRGAN_x4plus.pth -P experiments/pretrained_models

      (Note: If cant download run conda install main::pywget)


Step 7: Try by enhancing a single photo in your device. Import the photo to your Project directory and run

      python inference_realesrgan.py --model_path experiments/pretrained_models/RealESRGAN_x4plus.pth --input #your folder name with images in it --face_enhance --tile 100 --output #name of the folder you want to save the enhanced photo

Step 8: For videos we need to extract each frame from the video (Note: video should be in same directory as project)

      python extract.py --video #name of the video with .mp4 extension included --output #name of the extracted frames folder you want it to be 

Step 9: Now enhance each frame in the folder which has video frames extracted

      python inference_realesrgan.py --model_path experiments/pretrained_models/RealESRGAN_x4plus.pth --input #your folder name with frames in it --face_enhance --tile 100 --output #name of the folder you want to save the enhanced frames


Step 10: Now combine each frame to make a video

      python create_video.py -v --img_dir #name of the folder with enhanced frames --fps 24 --fourcc XVID --video #name of the final enhanced video with .mp4 extension included


      (Note: fps can be changed according to use cases)



I have run this in my PC which has 

1. AMD Ryzen 7 5800H
2. NVIDIA RTX 3060 Laptop GPU


If any queries please feel free to contact me by sending mail to ibrxhim.18@gmail.com
