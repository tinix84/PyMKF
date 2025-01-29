# Improved PyMKF Documentation Draft

Welcome to the PyMKF documentation! PyMKF is a Python wrapper for the MKF module of OpenMagnetics, designed to simplify the design and analysis of magnetic components. This library offers tools for core selection, winding design, and magnetic performance analysis, empowering engineers to optimize their projects efficiently.

## Table of Contents

- [Improved PyMKF Documentation Draft](#improved-pymkf-documentation-draft)
  - [Table of Contents](#table-of-contents)
  - [Quick Start](#quick-start)
  - [Installation Guide](#installation-guide)
    - [Requirements](#requirements)
      - [Core Dependencies](#core-dependencies)
      - [Build Dependencies](#build-dependencies)
    - [Installation Methods](#installation-methods)
      - [From PyPI (Recommended)](#from-pypi-recommended)
      - [From Source](#from-source)
  - [Examples](#examples)
  - [Best Practices](#best-practices)
  - [Development Guide](#development-guide)
    - [Setting Up Development Environment](#setting-up-development-environment)
    - [Project Structure](#project-structure)
  - [Features](#features)
  - [Contributing](#contributing)
  - [Troubleshooting](#troubleshooting)
    - [Common Issues](#common-issues)

---

## Quick Start

Here’s how to quickly get started with PyMKF:

```python
import pymkf

# Get available core materials
core_materials = pymkf.get_core_materials()
print("Available core materials:", core_materials)

# Find a specific core shape
core_shape = pymkf.find_core_shape_by_name("E65/32/27")
print("Selected core shape:", core_shape)
```

Each function’s parameters and outputs are detailed in the [API Documentation](#features).

---

## Installation Guide

### Requirements

#### Core Dependencies

- Python >= 3.7
- numpy >= 1.19.0
- pandas >= 1.3.0

#### Build Dependencies

- CMake >= 3.15
- C++ compiler with C++17 support
- pybind11

### Installation Methods

#### From PyPI (Recommended)

Install PyMKF using pip as suggested from [https://pypi.org/project/PyMKF/](https://pypi.org/project/PyMKF/)

```bash
pip install pymkf
```

#### From Source

For advanced users, clone and build from the GitHub repository:

```bash
git clone https://github.com/OpenMagnetics/PyMKF/PyMKF.git
cd PyMKF
python -m venv venv
source venv/bin/activate  # On Windows: .\venv\Scripts\activate
pip install -e .
```

---

## Examples

All the example are based on jupyter notebook to be executable from the web or tools like google Colab or Binder.

- [quickstart example](examples/quickstart.ipynb)
- [basic usage material](examples/basic_usage_material.ipynb)
- [basic usage core](examples/basic_usage_core.ipynb)
- basic usage winding
- basic design pwm inductor
- basic design resonant inductor
- basic design direct coupled inductor
- basic design indirect coupled inductor
- basic design transformer

---

## Best Practices

1. **Core Selection**:

   - Consider the operating temperature range and saturation limits.
   - Validate core losses against application requirements.

2. **Winding Design**:

   - Use appropriate wire types to minimize thermal and proximity effects.
   - Ensure winding fits within the bobbin.

3. **Loss Calculations**:

   - Include temperature and frequency dependencies.
   - Validate results with physical measurements when possible.

---

## Development Guide

### Setting Up Development Environment

1. Install build dependencies:

```bash
sudo apt-get install python3-dev cmake build-essential  # Linux
brew install cmake python                               # macOS
#TODO: Add Windows instructions
```

2. Clone the repository:

```bash
git clone https://github.com/tinix84/PyMKF.git
cd PyMKF
```

3. Set up a virtual environment:

```bash
python -m venv venv
source venv/bin/activate  # On Windows: .\venv\Scripts\activate
pip install -e ".[dev]"
```

### Project Structure

```text
PyMKF/
├── PyMKF.cpp         # Main C++ bindings
├── tests/            # Unit tests
├── examples/         # Example scripts
└── docs/             # Documentation and Jupyter notebooks
```

---

## Features

PyMKF offers a wide range of functionalities, including:

- Core material and shape selection
- Winding design and loss calculation
- Transformer optimization
- Thermal and frequency-dependent analysis
- Visualizations of magnetic fields and core geometries

For the full list of features, refer to the [API Documentation](#features).

---

## Contributing

1. Fork the repository and create a feature branch:

```bash
git checkout -b feature/new-feature
```

2. Commit and push your changes:

```bash
git commit -m "feat: add new feature"
git push origin feature/new-feature
```

3. Submit a pull request with a clear description.

---

## Troubleshooting

### Common Issues

1. **CMake Not Found**:

   - Ensure CMake is installed and added to your PATH.
   - To check if CMake is installed, run `cmake --version` in your terminal. If not installed, visit the [CMake download page](https://cmake.org/download/) and follow the instructions for your operating system.
   - On Windows, ensure the installation path is added to the PATH environment variable by selecting the option during installation or manually updating the PATH in system settings.

2. **Compiler Errors**:

   - Verify that your compiler supports C++17. Run `g++ --version` or `clang++ --version` to check your compiler version. For C++17 support, ensure the version is GCC 7.1 or higher, or Clang 5.0 or higher.
   - Use a simple test program to confirm compatibility:

     ```cpp
     #include <iostream>
     int main() {
         std::cout << "C++17 is supported!" << std::endl;
         return 0;
     }
     ```

     Compile using `g++ -std=c++17 test.cpp -o test` or equivalent.

3. **Python Version Mismatch**:

   - Ensure your Python version is 3.7 or higher. Use `python --version` or `python3 --version` to verify.
   - If using a virtual environment, activate it with the following commands:
     - On Linux/macOS: `source venv/bin/activate`
     - On Windows: `venv\Scripts\activate`
   - To switch between Python versions, consider using tools like `pyenv` (Linux/macOS) or `pyenv-win` (Windows). Check your Python version and virtual environment settings.

For additional help, consult the [Troubleshooting Guide](#troubleshooting-guide). You can also refer to the [official documentation](https://example.com/troubleshooting) for in-depth solutions to less common issues and advanced debugging tips.

---

Would you like further refinements or additional sections?

