# 📊 Visor: Efficient Dataset Management

![Visor Logo](https://via.placeholder.com/150x150.png?text=Visor)

[![Python Version](https://img.shields.io/badge/python-3.7%2B-blue.svg)](https://www.python.org/downloads/)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](https://opensource.org/licenses/MIT)
[![Build Status](https://img.shields.io/badge/build-passing-brightgreen.svg)](https://github.com/yourusername/visor)

Visor is a powerful Python library designed for efficient management and processing of large image datasets. It provides a streamlined solution for handling image data along with associated metadata and OCR information.

## 🚀 Features

- ✅ Efficient storage of image data, metadata, and OCR information
- ✅ Customizable image resizing options
- ✅ Fast reading and writing of large datasets
- ✅ Built-in data validation and error handling
- ✅ Easy-to-use API for dataset manipulation
- ✅ Support for compressed storage (optional)

## 📋 Table of Contents

- [Installation](#installation)
- [Quick Start](#quick-start)
- [Usage](#usage)
- [Configuration](#configuration)
- [API Reference](#api-reference)
- [Contributing](#contributing)
- [License](#license)

## 🔧 Installation
currently used as direct code, however I will be making this into a pip package at some point after doing some more tests, this is a very half cooked code for the time being.

## 🚀 Quick Start

Here's a simple example to get you started with Visor:

```python
from visor import Config, VisorWriter, VisorReader, ImageHandler

# Create a configuration
config = Config(
    data_type='image',
    max_entries_per_file=1000
)

# Write data
writer = VisorWriter(config, output_dir='./output')
handler = ImageHandler(config)

for image_path in image_paths:
    with open(image_path, 'rb') as f:
        image_data = f.read()
    entry = handler.process(image_data, image_path, ocr_data)
    writer.write_entries([entry])

writer.finalize()

# Read data
reader = VisorReader('./output/visor_metadata.json')
for entry in reader:
    # Process each entry
    pass
```

## 🔍 Usage

### Writing Data

To write data to a Visor file:

1. Create a `Config` object with your desired settings.
2. Initialize a `VisorWriter` with the config and output directory.
3. Use an `ImageHandler` to process your image data.
4. Write entries using the `write_entries` method.
5. Call `finalize()` to complete the writing process.

### Reading Data

To read data from a Visor file:

1. Create a `VisorReader` with the path to the metadata file.
2. Iterate over the reader to access entries.
3. Use methods like `get_entry()` or `get_metadata()` for random access.

## ⚙️ Configuration

The `Config` class allows you to customize Visor's behavior:

- `data_type`: Type of data ('image' or 'text')
- `image_dimensions`: Target dimensions for resizing (optional)
- `max_entries_per_file`: Maximum number of entries per Visor file
- `compression`: Enable/disable data compression

## 📚 API Reference

### VisorWriter

- `write_entries(entries)`: Write a list of entries to Visor files
- `finalize()`: Complete the writing process and generate metadata

### VisorReader

- `__iter__()`: Iterate over all entries
- `get_entry(index)`: Get a specific entry by index
- `get_metadata(index)`: Get metadata for a specific entry
- `print_summary()`: Display a summary of the dataset

### ImageHandler

- `process(data, original_name, ocr_data)`: Process image data and create an Entry

## 🤝 Contributing

We welcome contributions to Visor! Please see our [Contributing Guide](CONTRIBUTING.md) for more details.

## 📄 License

Visor is released under the MIT License. See the [LICENSE](LICENSE) file for more details.

---

📧 For any questions or support, please [open an issue](https://github.com/UYousafzai/datavisor/issues)