# CS256-AI-Human and Object Detection
# Group A

## Project Summary
The primary objective of our project was to improve human and object detection on low-light/dark images. We've used [EnlightenGAN](https://arxiv.org/abs/1906.06972) and have also used EnlightenGAN with different combinations of image filters such as Contrast Limited Adaptive Histogram Equalization (CLAHE) and Unsharp Mask (USM) to enhance low-light/dark images. The model that we used for human and object detection on these enlightened images was [Faster R-CNN](https://arxiv.org/abs/1506.01497) and found significant improvement in the performance. For more details, please refer to the [project report](https://github.com/ksheeraj/CS256-AI-ObjectDetection/blob/master/CS256_ProjectReport.pdf).

## INSTALLATION
The list below provides instructions on how to implement the deep learning models and image filters we used.
- Faster R-CNN
  - See [Faster R-CNN_AWS_Instructions.pdf](https://github.com/ksheeraj/CS256-AI-ObjectDetection/blob/master/Faster%20R-CNN_AWS_Instructions.pdf)
  - [Google COLAB Instructions](https://colab.research.google.com/drive/1RaWxgclMB8RpITo8Kci1qTecfm8iT61z#scrollTo=dq9GY37ml1kr)
- EnlightenGAN
  - See [EnlightenGAN_Setup.pdf](https://github.com/ksheeraj/CS256-AI-ObjectDetection/blob/master/EnlightenGAN_Setup.pdf)
- CLAHE & USM
  - See [CLAHE&UnsharpMask_Setup.pdf](https://github.com/ksheeraj/CS256-AI-ObjectDetection/blob/master/Filters/CLAHE%26UnsharpMask_Setup.pdf)
- Finetuned Faster R-CNN
  - [Google COLAB Instructions](https://colab.research.google.com/drive/1RaWxgclMB8RpITo8Kci1qTecfm8iT61z#scrollTo=dq9GY37ml1kr)

## Architecture Diagrams

![alt text](https://github.com/ksheeraj/CS256-AI-ObjectDetection/blob/master/Architecture_Diagrams/Architecture_Diagram_1.png)

Based on this diagram, we are running inference on low-light/dark images, taken from the Exclusively Dark dataset, using the Faster R-CNN model from Detectron2. **The intent of this experiment is to examine how Faster R-CNN performs on a low-light/dark image.**

![alt text](https://github.com/ksheeraj/CS256-AI-ObjectDetection/blob/master/Architecture_Diagrams/Architecture_Diagram_2.png)

Based on this diagram, we are feeding in a few low-light/dark images into EnlightenGAN and then feeding in the fake images generated by EnlightenGAN into the same Faster R-CNN model as the one used in Architecture Diagram 1. **The intent of this experiment is to examine how Faster R-CNN performs on enlightened/enhanced images.**

![alt text](https://github.com/ksheeraj/CS256-AI-ObjectDetection/blob/master/Architecture_Diagrams/Architecture_Diagram_3.png)

Based on this diagram, we are feeding in a few low-light/dark images into an image filter, called CLAHE. This filter will compute several histograms, each corresponding to a distinct section of the image, and use them to redistribute the lightness values of the image. Then the image outputs of this filter will be fed into the same Faster R-CNN model that we have been using so far. **The intent of this experiment is to examine how Faster R-CNN performs on low-light/dark images that have been fed through an image filter.**

![alt text](https://github.com/ksheeraj/CS256-AI-ObjectDetection/blob/master/Architecture_Diagrams/Architecture_Diagram_4.png)

As showcased in this diagram, the first two steps are a subset of Architecture Diagram 3. For this experiment, we will be taking the output images produced by the CLAHE filter and feed it through EnlightenGAN. Since EnlightenGAN adds noise to its output images, we feed the output images from EnlightenGAN into the CLAHE filter to filter out the noise. Then the output images from the CLAHE filter are fed into the Faster R-CNN model that we have been working with so far. **The intent of this experiment is to examine how Faster R-CNN performs on images that have been applied with an image filter before and after EnlightenGAN.**

![alt text](https://github.com/ksheeraj/CS256-AI-ObjectDetection/blob/master/Architecture_Diagrams/Architecture_Diagram_5.png)

As showcased in this diagram, the last three steps are a subset of Architecture Diagram 4. For this experiment, we are feeding in a few low-light/dark images into an image filter, called USM. This filter will amplify the high-frequency components of an image and produce an output with better contrast and brightness. We will be taking the output images produced by the USM filter and feed it through EnlightenGAN and follow Architecture Diagram 4 thereafter. **The intent of this experiment is to examine how Faster R-CNN performs on images that have been applied with a combination of image filters before and after EnlightenGAN.**

![alt text](https://github.com/ksheeraj/CS256-AI-ObjectDetection/blob/master/Architecture_Diagrams/Architecture_Diagram_6.png)

## Quickstart
See [EnlightenGAN_Setup.pdf](https://github.com/ksheeraj/CS256-AI-ObjectDetection/blob/master/EnlightenGAN_Setup.pdf), or the [Colab Notebook](https://colab.research.google.com/drive/1RaWxgclMB8RpITo8Kci1qTecfm8iT61z#scrollTo=dq9GY37ml1kr).

## Citing Detectron2 and EnlightenGAN

```@misc{wu2019detectron2,
  author =       {Yuxin Wu and Alexander Kirillov and Francisco Massa and
                  Wan-Yen Lo and Ross Girshick},
  title =        {Detectron2},
  howpublished = {\url{https://github.com/facebookresearch/detectron2}},
  year =         {2019}
}

  @article{jiang2019enlightengan,
  title={EnlightenGAN: Deep Light Enhancement without Paired Supervision},
  author={Jiang, Yifan and Gong, Xinyu and Liu, Ding and Cheng, Yu and Fang, Chen and Shen, Xiaohui and Yang, Jianchao and Zhou, Pan and Wang, Zhangyang},
  journal={arXiv preprint arXiv:1906.06972},
  year={2019}
}
```
## About:

This page(code, report and presentation) is the Group A submission for the final project of the course CS256: Topics in Artificial Intelligence, Section 2 at San Jose State University. Led by Instructor: Mashhour Solh, Ph.D.

The group members are: Anket Sah, Amala Chirayil, Ksheeraj Sai Vepuri, Kriti Gupta, Sanmesh Bhosale.

The code maybe used for educational and commercial use under no warranties. For questions on this project and code please reach out to: amalachirayil@gmail.com.

Credits:

This project was conducted with free credits provided by AWS Educate Team. Thank you AWS!
