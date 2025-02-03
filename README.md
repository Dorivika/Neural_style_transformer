## Overview
This project implements Neural Style Transfer using PyTorch, based on the seminal paper ["A Neural Algorithm of Artistic Style"](https://arxiv.org/abs/1508.06576) by Gatys et al. The implementation uses a pre-trained VGG19 network to transfer artistic styles from one image to another.

## Features
- VGG19-based style transfer implementation
- Customizable content and style layer selection
- Support for GPU acceleration
- Configurable optimization parameters
- Real-time loss monitoring
- Progress visualization options

## Requirements
```
- Python 3.7+
- PyTorch
- torchvision
- Pillow (PIL)
- matplotlib
- CUDA (optional, for GPU support)
```

## Installation
1. Clone this repository:
```bash
git clone https://github.com/Dorivika/Neural_style_transformer.git
cd Neural_style_transformer
```

2. Install dependencies:
```bash
pip install torch torchvision pillow matplotlib
```

## Usage
1. Place your content image in the `content_images` directory
2. Place your style image in the `style_images` directory
3. Run the script:
```bash
python style_transfer.py
```

### Advanced Usage
You can customize the style transfer by modifying these parameters:
```python
iterations = 200    # Number of optimization steps
lr = 1e-2          # Learning rate
alpha = 1          # Content loss weight
beta = 1           # Style loss weight
```

## Implementation Details

### Key Components

1. **VGG19 Model Modification**
   - Uses pretrained VGG19 architecture
   - Replaces MaxPool layers with AvgPool for better results
   - Features are extracted from specific layers for content and style representation

2. **Loss Functions**
   - Content Loss: Mean squared error between content and generated features
   - Style Loss: Mean squared error between Gram matrices of style and generated features
   - Total Loss: Weighted combination of content and style losses

3. **Optimization**
   - Uses Adam optimizer
   - Gradient descent on the generated image
   - Content image used as initialization

## Parameters Explanation

```python
iterations = 200  # Total optimization steps
lr = 1e-2        # Learning rate for optimizer
alpha = 1        # Weight for content loss
beta = 1         # Weight for style loss
```

- Higher learning rates (lr) will result in more dramatic style transfers
- Adjusting alpha/beta ratio changes the balance between content and style preservation

## Results
The generated image will be saved as `gen.png` in the project directory. Intermediate results can be visualized by setting `show_images=True` in the `transfer_style` function.

## Tips for Better Results
1. Image size affects both quality and processing time. Start with smaller images (512px) for faster iterations
2. Experiment with different learning rates:
   - Higher rates (1e-2) for dramatic style changes
   - Lower rates (1e-3 or 1e-4) for subtle effects
3. Adjust iterations based on your needs:
   - 200 iterations for quick results
   - 500+ iterations for higher quality

## License
[MIT License](https://choosealicense.com/licenses/mit/)