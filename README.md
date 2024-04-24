# imagecorruptions
This repository offers a collection of image corruptions designed to evaluate the robustness of neural networks. These corruptions serve dual purposes: enhancing training data through augmentation and assessing network performance against unforeseen disruptions.

## Installation and Usage
To set up the environment and install dependencies:

1. Clone the repository:
```bash
git clone https://github.com/ahosnyyy/image_corruptions.git
```

2. Navigate into the cloned repository directory:
```bash
cd image_corruptions
```

3. Create a Conda environment:
```bash
conda create --name image_corruptions python=3.8
```

4. Activate the newly created environment:
```bash
conda activate image_corruptions
```

5. Install dependencies from the requirements file:
```bash
pip install -r requirements.txt
```

An example of how to use the corruption function is given below:
```python
from imagecorruptions import corrupt
...
corrupted_image = corrupt(image, corruption_name='gaussian_blur', severity=1)
...
```
Looping over all available corruptions can be done either by name or by index:
```python
# via name
from imagecorruptions import get_corruption_names
for corruption in get_corruption_names():
    for severity in range(5):
        corrupted = corrupt(image, corruption_name=corruption, severity=severity+1)
        ...

# via number:
for i in range(15):
    for severity in range(5):
        corrupted = corrupt(image, corruption_number=i, severity=severity+1)
        ...
```

Note that the first 15 image corruptions are the common corruptions (the ones you get via `get_corruption_names()`). If you really wish to use these as data augmentation, there exist four additional validation corruptions which can be accessed via `get_corruption_names('validation')` which should then be used to test the corruption robustness of the trained model.
