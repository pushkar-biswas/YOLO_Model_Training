# YOLO_Model_Training
Instructions to train a YOLO model utilizing GPU(NVIDIA)

## Prerequisite : Install CUDA with CUDNN support to utilize GPU for faster train and inference
	type " nvcc --version " on terminal to check the cuda version installed on the system. Same for windows and Linux

### Create a python virtual environment(if any error occurs then you can delete the whole folder without affecting any other packages)
	For windows : python -m venv /path/to/new/virtual/environment
	For Linux : sudo pip3 install virtualenv
		    virtualenv venv                        * Note : venv is the folder name of the virtaul environment. Folder will be created at current directory of the terminal

### Activate the environment :
	For windows : C:\path_to_virtual_env\Scripts\activate.bat
	For Linux : source name_of_venv_folder/bin/activate        * Note : if current directory is inside venv_folder then write source bin/activate

### Install Pytorch (This should be done before installing Ultralytics)
	Download the pytorch version according to the cuda verison.  *Note : Check CUDA,Pytorch and Python compatiblity with each other
	Go to https://pytorch.org/get-started/previous-versions/
	Use Ctrl + F to seach for the cuda version you need
	Copy the pip code and paste it in the terminal
	pip install torch==2.2.2 torchvision==0.17.2 torchaudio==2.2.2 --index-url https://download.pytorch.org/whl/cu118 (This link is for pytorch version 2.2.2 for cuda version 11.8)

### Install Ultralytics :
	Same for windows and Linux : pip install ultralytics

### After installation of ultralytics, change data.yaml path according to the following path :

	configure dataset file path in C:\Users\pushk\AppData\Roaming\Ultralytics(windows)
	configure dataset file path in /home/<system_name>/.config/Ultralytics(ubuntu)

### For training :
	Note: Please run the command from project directory. For example, if project is created in 'C:\yolo_training' then while running the command line be sure that you are in 'C:\yolo_training'.
	for classification : yolo classify train data=mnist160 model=yolov8n-cls.pt epochs=100 imgsz=64
	for detection : yolo task=detect mode=train model=yolov8n.pt data= data.yaml epochs=100 imgsz=640 plots=True device=0
	for segmentation : yolo task=segment mode=train model=yolov8n-seg.pt data= data.yaml epochs=100 imgsz=640 plots=True device=0
