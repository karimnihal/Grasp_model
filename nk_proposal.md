# Project Proposal

### Objectives and Goals

Our project aims to address the challenge of vision-based robotic grasp detection, specifically training a deep learning model to predict optimal grasp positions from object images. The primary goal is enabling robots to autonomously identify and successfully execute grasps on diverse, previously unseen objects, significantly enhancing robotic autonomy in unstructured environments such as warehouses or homes.

### Problem & Approach

The core problem is enabling robotic perception to reliably interpret visual information and determine viable grasp strategies. We will approach this as a supervised deep learning task using Convolutional Neural Networks (CNNs). Specifically, we plan to implement a CNN model that predicts grasp rectangles (position, size, orientation) directly from input images, leveraging transfer learning and extensive data augmentation to address limited dataset size.

### Data Selection

We will primarily use the [Cornell Grasping Dataset (CGD)](https://www.kaggle.com/datasets/oneoneliu/cornell-grasp), a widely utilized benchmark dataset tailored for robotic grasp detection. The CGD includes annotated grasp positions on a variety of everyday objects, making it highly suitable for training robust grasp detection models. Additionally, we might employ a subset of the larger synthetic [Jacquard Dataset](https://jacquard.liris.cnrs.fr/index.php) for pretraining or additional augmentation to enhance model generalization capabilities - however, access must be granted through official channels (see note below).

### Data Description

The CGD contains approximately 885 RGB-D images featuring 240 different household items, with over 8,000 labeled grasps. Each grasp annotation specifies a rectangle defined by its position, dimensions, and orientation suitable for a parallel-jaw robot gripper. Images typically depict single objects against plain backgrounds, annotated by human experts to indicate both successful (positive) and unsuccessful (negative) grasp regions.

**Preprocessing:**
Data preprocessing will involve extensive augmentation, including rotations, translations, scaling, and brightness adjustments, to increase effective dataset size and prevent overfitting. We may use RGB, depth images, or a combination, carefully normalizing inputs to suit CNN architectures.

### Note

Jacquard grasping dataset must be requested by an official academic personnel/permanent member - so access may be limited.

From EULA - "...must be signed by a person with a permanent position at an academic institute (the signee). Up to five other researchers affiliated with the same institute for whom the signee is responsible..."
