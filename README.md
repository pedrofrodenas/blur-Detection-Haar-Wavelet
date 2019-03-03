# Blur Detection Haar Wavelet opencv-python
Blur Detection of Digital Images using Haar Wavelet Transform. This is the implementation of this [paper](http://tonghanghang.org/pdfs/icme04_blur.pdf)

## Prerequisites
* [Python3](https://www.python.org/)
* [opencv-python](https://pypi.python.org/pypi/opencv-python)
* [PyWavelets](https://pywavelets.readthedocs.io/en/latest/)

## How to use
Make sure python3 and pip is installed. Then, install cv2 and PyWavelets.
```bash
# install opencv-python
pip install cv2
# install PyWavelets
pip install PyWavelets
```

To run the python script with the sample images uploaded to this repo.
```bash
python blur_wavelet.py -i images/blur
```

The output will be

```bash
images/blur/Original_391.jpg, Per: 0.00011, blur extent: 41.142, is blur: True
images/blur/Original_426.jpg, Per: 0.00000, blur extent: 81.158, is blur: True
images/blur/Original_292.jpg, Per: 0.00000, blur extent: 50.951, is blur: True
images/blur/Original_244.jpg, Per: 0.00000, blur extent: 299.500, is blur: True
images/blur/Original_297.jpg, Per: 0.00282, blur extent: 10.708, is blur: False
images/blur/Original_254.jpg, Per: 0.00017, blur extent: 1445.000, is blur: True
images/blur/Original_6.jpg, Per: 0.00000, blur extent: 9.936, is blur: True
images/blur/Original_5.jpg, Per: 0.00032, blur extent: 12.265, is blur: True
images/blur/Original_359.jpg, Per: 0.00000, blur extent: 121.937, is blur: True
images/blur/Original_217.jpg, Per: 0.00016, blur extent: 28.323, is blur: True
```

The [paper](http://tonghanghang.org/pdfs/icme04_blur.pdf) defines two parameters in order to configure the algorithm. The first is **threshold**. It is used to select if a pixel of Haar transform image is considered as Edge Point. Default value is 35. If you select a smaller threshold, it is more likely an image to be classified as blur.

The default **threshold** is 35. You can define it by adding the parameter in the bash call. In the following call to the script we select 25 as threshold.
```bash
python blur_wavelet.py -i images/noblur --threshold 25
```
The output will be

```bash
images/noblur/DSCN0593.JPG, Per: 0.00486, blur extent: 1.878, is blur: False
images/noblur/DSCN6481.JPG, Per: 0.00108, blur extent: 3.424, is blur: False
images/noblur/DSC02100.JPG, Per: 0.00181, blur extent: 0.974, is blur: False
images/noblur/DSC00700.JPG, Per: 0.00782, blur extent: 1.117, is blur: False
images/noblur/DSC05345.JPG, Per: 0.00424, blur extent: 0.741, is blur: False
images/noblur/DSC01910.JPG, Per: 0.00694, blur extent: 1.269, is blur: False
images/noblur/IMG_0066.JPG, Per: 0.00250, blur extent: 4.715, is blur: False
images/noblur/IMG_0487.JPG, Per: 0.01155, blur extent: 1.795, is blur: False
images/noblur/DSC05405.JPG, Per: 0.01503, blur extent: 0.645, is blur: False
images/noblur/DSCN0375.JPG, Per: 0.00356, blur extent: 2.422, is blur: False
```

#### Save output as .JSON

In order to save the output as .JSON, run the script with the flag **-s SAVE_PATH.json**
