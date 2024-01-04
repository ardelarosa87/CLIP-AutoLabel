# Automated Data Labeling Using CLIP
![Pipeline Overview](images_for_documentation/Overall_pipeline_view.png)


## Introduction

Welcome to my repository, where I address a critical challenge in the field of image classification and object detection tasks: the scarcity of accurately labeled data. Our innovative pipeline is designed to automate the data labeling process by harnessing the power of OpenAI's CLIP model, offering a more efficient alternative to traditional methods.

## The Challenge

In projects involving image classification and object detection mechanisms like YOLO (You Only Look Once), obtaining accurately labeled data is often a significant bottleneck. Manually labeling datasets can be labor-intensive and time-consuming, impeding the development and accuracy of machine learning models.

## Solution

The pipeline tackles this challenge by automating the data labeling process, with the OpenAI CLIP model at its core. Known for its ability to understand and categorize images based on textual descriptions, CLIP enables us to correlate text and images effectively.

### CLIP

CLIP (Contrastive Language–Image Pre-training) is a neural network, which efficiently learns visual concepts from natural language supervision. CLIP is trained on a vast dataset of images and
corresponding textual descriptions. This training enables the model to learn the relationships between text and images, essentially understanding how specific visual elements in images correlate with the words and phrases used to describe them. By combining text and image CLIP has a broad generalization from the training data to a wide variety of real-world tasks, even those it wasn't explicitly trained on. CLIP can applied to visual classification by providing the names and visual categories to be recognized, similar to the `zero-shot` capabilities of `GPT-2` and `GPT-3`. 

![CLIP OVerview](images_for_documentation/Clip_Overview.png)
**OpenAI CLIP Research Page:** [OpenAI CLIP Research](https://openai.com/research/clip)

### CLIP Evaluation

To initiate the project, I'll begin with an evaluation of OpenAI's CLIP model using the PASCAL Visual Object Classes (VOC) dataset. This dataset comprises 5823 images, each annotated with bounding boxes and class labels. The first step involves cropping these images within their bounding boxes to create a tailored dataset.

Next, I implement a stratified sampling strategy, selecting 100 samples from each class to ensure a balanced representation. These samples are then processed through CLIP, accompanied by text embeddings, to perform classification.

From this procedure, a dataset of 2000 images is compiled. Comparing CLIP's labeling against the original manual annotations from the VOC dataset, an accuracy rate of 79.3% is achieved. Intriguingly, CLIP provides more accurate labels than the original ground truth for some images, highlighting its qualitative effectiveness.

### Advantages Over Manual Labeling

Despite the need for some manual oversight, this automated approach is substantially more efficient than the traditional method of manually identifying object regions, extracting these regions, and assigning labels individually. By reducing the labor-intensive aspects of data preparation, the system facilitates a quicker and more streamlined path towards preparing datasets for training machine learning models by leveraging the zero shot capabilities from CLIP.


## How It Works

The process starts with generating region proposals from some other network such as YOLO or Faster-RCNN. Then descriptive prompts for images in the dataset are created. These prompts along with the images are fed into CLIP, which categorizes the images accordingly. This not only accelerates labeling but also enhances label accuracy and diversity.

## Key Findings and Highlights

- **Faster R-CNN Integration:** Utilizing Faster R-CNN, our pipeline generated numerous region proposals, which were refined using CLIP.
- **Robust Detection:** CLIP's effectiveness in accurately classifying low-resolution images and complex scenes was noteworthy.
- **Efficiency:** This approach significantly reduces the time and automates effort required for data preparation, compared to manual labeling.

## End Goal

The goal is to streamline data preparation for image classification and object detection tasks, expediting the development of machine learning models with well-labeled, diverse datasets.


# Conclusion

## Experiment
The aim of the experiment was to automate the process of labeling images featuring bees in flight. To this end, four images depicting bees, sourced from Google, were selected and evaluated for the study.

## Insights from the Faster-RCNN and CLIP Integration

In the experiment, Faster-RCNN, set with a confidence threshold of 0.7, generated 52 region proposals on four different images containing bees. However, these initial proposals were not accurately classified and included regions with irrelevant content or mere backgrounds, alongside those potentially containing bees.

### Refinement Using CLIP

When these cropped region proposals were processed through CLIP, equipped with targeted text embeddings `["a photo of a bee in flight.", "mostly background"]
`, a remarkable outcome was observed. CLIP successfully identified and classified 18 out of these 52 regions as containing bees. Upon reviewing the output, it is evident that all 18 selected images indeed contain bees while the others were , validating the efficacy of the approach.

### Notable Observations and Considerations

An intriguing aspect of the results was the ability of the system to accurately identify bees even in images with very low pixel resolution. This highlights the robustness of CLIP in handling varied image qualities. However, it's worth noting a potential limitation: the presence of other insects in the images could pose a challenge to the specificity of the classification in regions with low pixel resolution. This is an area that warrants further exploration to enhance the model's accuracy in more complex scenarios. Additional pre-processing methods might be beneficial, like upsampling the low-resolution cropped regions to enhance their quality. This could lead to higher resolution images, thereby ensuring the dataset's overall quality is improved. Moreover, incorporating images with a low pixel count of the target class could expand the dataset's diversity. This approach may enhance the model's robustness, enabling it to detect the same class of objects effectively, even from greater distances.


## Resources

To delve deeper into the CLIP model and its applications:

1. **OpenAI CLIP Research Page:** [OpenAI CLIP Research](https://openai.com/research/clip)
2. **CLIP GitHub Repository:** [CLIP on GitHub](https://github.com/openai/CLIP/tree/main)

## Explore and Contribute

I invite you to explore this repository, contribute, and leverage this pipeline for your image
classification and object detection projects.

