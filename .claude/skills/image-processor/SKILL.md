---
name: image-processor
description: Process and enhance images with AI. Resize, compress, convert formats, remove backgrounds, upscale images, and apply filters. Use when working with images, photo editing, or image optimization.
allowed-tools: Read, Grep, Glob, Bash
---

# Image Processor

Advanced image processing toolkit with AI-powered features for manipulation, enhancement, and optimization.

## What this Skill does

- Resize and compress images
- Convert between formats (JPEG, PNG, WebP, AVIF)
- AI-powered image enhancement and upscaling
- Background removal and replacement
- Object detection and segmentation
- Watermark addition and removal
- Batch processing with parallelization
- Color correction and filtering
- Generate thumbnails and previews

## Requirements

Install required packages:
```bash
pip install Pillow opencv-python
pip install numpy

# For AI features
pip install rembg
pip install waifu2x-ncnn-vulkan  # For upscaling
```

## How to use

### Basic image operations
```python
from PIL import Image

# Open image
image = Image.open('input.jpg')

# Resize
resized = image.resize((800, 600))

# Compress and save
resized.save('output.jpg', quality=85, optimize=True)

# Convert format
image.save('output.png', format='PNG')
```

### Batch processing
```python
import os
from PIL import Image

input_dir = 'images/'
output_dir = 'processed/'

for filename in os.listdir(input_dir):
    if filename.lower().endswith(('.png', '.jpg', '.jpeg')):
        image = Image.open(os.path.join(input_dir, filename))
        # Process image
        processed = image.resize((800, 600))
        processed.save(os.path.join(output_dir, filename))
```

### Remove background
```bash
pip install rembg
python -c "
from rembg import remove
from PIL import Image

with open('input.jpg', 'rb') as input_file:
    input_data = input_file.read()
    output_data = remove(input_data)

with open('output.png', 'wb') as output_file:
    output_file.write(output_data)
"
```

### Image upscaling
```bash
pip install waifu2x-ncnn-vulkan
waifu2x-ncnn-vulkan -i input.jpg -o output.jpg --scale 2 --noise 1
```

### Apply filters
```python
from PIL import ImageFilter
from PIL import ImageEnhance

image = Image.open('input.jpg')

# Blur
blurred = image.filter(ImageFilter.BLUR)

# Enhance contrast
enhancer = ImageEnhance.Contrast(image)
enhanced = enhancer.enhance(1.5)

# Adjust brightness
enhancer = ImageEnhance.Brightness(image)
bright = enhancer.enhance(1.2)
```

### Generate thumbnail
```python
from PIL import Image

image = Image.open('input.jpg')
image.thumbnail((300, 300), Image.Resampling.LANCZOS)
image.save('thumbnail.jpg', quality=85)
```

## Examples

When to use this Skill:
- "Resize and compress these images for web"
- "Remove the background from this photo"
- "Convert all images to WebP format"
- "Upscale this low-resolution image"
- "Apply a blur effect to these photos"
- "Generate thumbnails for this image gallery"

## Batch Processing Script

Create a script for batch operations:
```python
#!/usr/bin/env python3
import os
import sys
from PIL import Image

def process_images(input_dir, output_dir, size=(800, 600), quality=85):
    os.makedirs(output_dir, exist_ok=True)

    for filename in os.listdir(input_dir):
        if filename.lower().endswith(('.png', '.jpg', '.jpeg')):
            input_path = os.path.join(input_dir, filename)
            output_path = os.path.join(output_dir, filename)

            with Image.open(input_path) as img:
                img_resized = img.resize(size, Image.Resampling.LANCZOS)
                img_resized.save(output_path, quality=quality, optimize=True)

            print(f"Processed: {filename}")

if __name__ == "__main__":
    process_images(sys.argv[1], sys.argv[2])
```

Usage:
```bash
python process.py input_folder output_folder
```

## Tips

- Use WebP for web images (better compression)
- Maintain aspect ratio when resizing
- Use appropriate quality settings for different use cases
- Process images in batches for efficiency
- Use multiprocessing for large datasets
