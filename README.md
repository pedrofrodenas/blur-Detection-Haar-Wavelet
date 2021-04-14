# Blur Detection Haar Wavelet opencv-python
Blur Detection of Digital Images using Haar Wavelet Transform. This is the implementation of this [paper](http://tonghanghang.org/pdfs/icme04_blur.pdf)

## Prerequisites
* [Python3](https://www.python.org/)
* [opencv-python](https://pypi.python.org/pypi/opencv-python)
* [PyWavelets](https://pywavelets.readthedocs.io/en/latest/)

Make sure python3 and pip is installed. Then, run in current working directory

```bash
$ pip install -r requirements.txt
```

## How to use

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
#### Configure the edge threshold

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

#### Configure the decision threshold

In the [paper](http://tonghanghang.org/pdfs/icme04_blur.pdf) is called **MinZero**. If **Per** is smaller than **MinZero** the image is classified as blur. The default value is 0.001 .
In order to configure the **MinZero** threshold, run the script with the flag **-d MIN_ZERO**

```bash
python blur_wavelet.py -i images/noblur -d 0.005
```

The output will be

```bash
images/noblur/DSCN0593.JPG, Per: 0.00459, blur extent: 2.029, is blur: True
images/noblur/DSCN6481.JPG, Per: 0.00068, blur extent: 5.012, is blur: True
images/noblur/DSC02100.JPG, Per: 0.00135, blur extent: 1.786, is blur: True
images/noblur/DSC00700.JPG, Per: 0.00782, blur extent: 1.405, is blur: False
images/noblur/DSC05345.JPG, Per: 0.00343, blur extent: 0.929, is blur: True
images/noblur/DSC01910.JPG, Per: 0.00647, blur extent: 1.697, is blur: False
images/noblur/IMG_0066.JPG, Per: 0.00205, blur extent: 5.373, is blur: True
images/noblur/IMG_0487.JPG, Per: 0.01045, blur extent: 2.182, is blur: False
images/noblur/DSC05405.JPG, Per: 0.01310, blur extent: 0.775, is blur: False
images/noblur/DSCN0375.JPG, Per: 0.00296, blur extent: 2.865, is blur: True
```

The prediction fails in this case.


#### Save output as .JSON

In order to save the output as .JSON, run the script with the flag **-s SAVE_PATH.json** . Example: save .json output in the project directory as output.json:

```bash
python blur_wavelet.py -i images/blur -s output.json
```

Checking the .json file:

```json
[
    {
        "blur extent": 41.14235294117647,
        "input_path": "images/blur/Original_391.jpg",
        "is blur": true,
        "per": 0.0001104911330865698
    },
    {
        "blur extent": 81.15789473684211,
        "input_path": "images/blur/Original_426.jpg",
        "is blur": true,
        "per": 0.0
    }
]
```

## Acknowlegements

#### Dataset
The sample images have been taken from this [blur image dataset](https://mklab.iti.gr/results/certh-image-blur-dataset/)

E. Mavridaki, V. Mezaris, "No-Reference blur assessment in natural images using Fourier transform and spatial pyramids", Proc. IEEE International Conference on Image Processing (ICIP 2014), Paris, France, October 2014.

The dataset consists of undistorted, naturally-blurred and artificially-blurred images for image quality assessment purposes. Download the dataset from here: [http://mklab.iti.gr/files/imageblur/CERTH_ImageBlurDataset.zip](http://mklab.iti.gr/files/imageblur/CERTH_ImageBlurDataset.zip)


#### Paper

This algorithm is based on this [paper](http://tonghanghang.org/pdfs/icme04_blur.pdf)

Tong, Hanghang & Li, Mingjing & Zhang, Hongjiang & Zhang, Changshui. (2004). Blur detection for digital images using wavelet transform. IEEE International Conference on Multimedia and EXPO. 1. 17 - 20 Vol.1. 10.1109/ICME.2004.1394114. 

#### Github Users

Thanks to the user [@a-hasan-gar](https://github.com/a-hasan-gar) for noticing an implementation error and fixing it.

## License
(c) 2019 Pedro Rodenas. MIT License

