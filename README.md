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
images/blur/Original_391.jpg, Per: 0.0001104911330865698, blur extent: 41.14235294117647, is blur: True
images/blur/Original_426.jpg, Per: 0.0, blur extent: 81.15789473684211, is blur: True
images/blur/Original_292.jpg, Per: 0.0, blur extent: 50.951219512195124, is blur: True
images/blur/Original_244.jpg, Per: 0.0, blur extent: 299.5, is blur: True
images/blur/Original_297.jpg, Per: 0.002821792923811591, blur extent: 10.708385481852316, is blur: False
images/blur/Original_254.jpg, Per: 0.0001729804532087874, blur extent: 1445.0, is blur: True
images/blur/Original_6.jpg, Per: 0.0, blur extent: 9.93574297188755, is blur: True
images/blur/Original_5.jpg, Per: 0.00031969309462915604, blur extent: 12.264705882352942, is blur: True
images/blur/Original_359.jpg, Per: 0.0, blur extent: 121.93675889328063, is blur: True
images/blur/Original_217.jpg, Per: 0.00016038492381716118, blur extent: 28.323383084577113, is blur: True
```
