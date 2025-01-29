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
    - [Core Selection](#core-selection)
    - [Winding Design](#winding-design)
    - [Advanced Examples](#advanced-examples)
      - [Transformer Design](#transformer-design)
  - [Best Practices](#best-practices)
  - [Development Guide](#development-guide)
    - [Setting Up Development Environment](#setting-up-development-environment)
    - [Project Structure](#project-structure)
  - [Features overview](#features-overview)
  - [Contributing](#contributing)
  - [Troubleshooting](#troubleshooting)
    - [Common Issues](#common-issues)
  - [Features](#features)
- [TODO](#todo)

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

# Calculate core losses
core_data = {...}  # Replace with core specifications
coil_data = {...}  # Replace with coil specifications
inputs_data = {...}  # Replace with input parameters
models_data = {...}  # Replace with model specifications
core_losses = pymkf.calculate_core_losses(core_data, coil_data, inputs_data, models_data)
print("Core losses:", core_losses)
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
Install PyMKF using pip:

```bash
pip install pymkf
```

#### From Source
For advanced users, clone and build from the GitHub repository:

```bash
git clone https://github.com/tinix84/PyMKF.git
cd PyMKF
python -m venv venv
source venv/bin/activate  # On Windows: .\venv\Scripts\activate
pip install -e .
```

---

## Examples

### Core Selection

Select and analyze magnetic cores with ease:

```python
import pymkf

# List all available core shapes
cores = pymkf.get_core_shapes()
print("Available cores:", cores)

# Find and analyze a specific core
core = pymkf.find_core_shape_by_name("E65/32/27")
processed_data = pymkf.calculate_core_data(core, include_material_data=True)
print("Core parameters:", processed_data)
```

### Winding Design

Design efficient windings to minimize losses:

```python
# Define winding parameters
winding_data = {
    "number_turns": 20,
    "wire_type": "round",
    "wire_name": "AWG24"
}

# Calculate winding losses
losses = pymkf.calculate_winding_losses(magnetic_data, operating_point, temperature=25)
print("Winding losses:", losses)
```

### Advanced Examples

#### Transformer Design
Optimize transformers for specific applications:

```python
# Define transformer specifications
transformer_specs = {
    "primary_turns": 100,
    "secondary_turns": 10,
    "core_type": "E65/32/27"
}

# Perform full transformer analysis
results = pymkf.design_transformer(transformer_specs)
print("Transformer design results:", results)
```

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
├── src/pymkf/           # Source code
│   ├── core.cpp         # Main C++ bindings
│   ├── wrappers/        # C++ wrapper headers
│   └── utils.py         # Python utilities
├── tests/               # Unit tests
├── examples/            # Example scripts
└── docs/                # Documentation and Jupyter notebooks
```

---

## Features overview

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

2. **Compiler Errors**:
   - Verify that your compiler supports C++17.

3. **Python Version Mismatch**:
   - Check your Python version and virtual environment settings.

For additional help, consult the [Troubleshooting Guide](#troubleshooting-guide).

---

Would you like further refinements or additional sections?


## Features
Currently, PyMKF provides the following features:

- 'add_margin_to_section_by_index',
- 'are_sections_and_layers_fitting',
- 'calculate_advised_cores',
- 'calculate_advised_magnetics',
- 'calculate_basic_processed_data',
- 'calculate_bobbin_data',
- 'calculate_core_data',
- 'calculate_core_gapping',
- 'calculate_core_geometrical_description',
- 'calculate_core_losses',
- 'calculate_core_processed_description',
- 'calculate_dc_losses_per_meter',
- 'calculate_dc_resistance_per_meter',
- 'calculate_effective_current_density',
- 'calculate_effective_skin_depth',
- 'calculate_gap_reluctance',
- 'calculate_gapping_from_number_turns_and_inductance',
- 'calculate_harmonics',
- 'calculate_induced_current',
- 'calculate_induced_voltage',
- 'calculate_inductance_from_number_turns_and_gapping',
- 'calculate_instantaneous_power',
- 'calculate_insulation',
- 'calculate_magnetic_field_strength_field',
- 'calculate_number_turns',
- 'calculate_number_turns_from_gapping_and_inductance',
- 'calculate_ohmic_losses',
- 'calculate_processed',
- 'calculate_proximity_effect_losses',
- 'calculate_reflected_primary',
- 'calculate_reflected_secondary',
- 'calculate_rms_power',
- 'calculate_shape_data',
- 'calculate_skin_ac_factor',
- 'calculate_skin_ac_losses_per_meter',
- 'calculate_skin_ac_resistance_per_meter',
- 'calculate_skin_effect_losses',
- 'calculate_skin_effect_losses_per_meter',
- 'calculate_winding_losses',
- 'check_if_fits',
- 'check_requirement',
- 'create_basic_bobbin',
- 'create_waveform',
- 'delimit_and_compact',
- 'extract_column_names',
- 'extract_map_column_names',
- 'extract_operating_point',
- 'find_bobbin_by_name',
- 'find_core_material_by_name',
- 'find_core_shape_by_name',
- 'find_insulation_material_by_name',
- 'find_wire_by_name',
- 'find_wire_material_by_name',
- 'get_available_coil_alignments',
- 'get_available_core_manufacturers',
- 'get_available_core_materials',
- 'get_available_core_shape_families',
- 'get_available_core_shapes',
- 'get_available_shape_families',
- 'get_available_winding_orientations',
- 'get_available_wire_standards',
- 'get_available_wire_types',
- 'get_available_wires',
- 'get_bobbin_names',
- 'get_bobbins',
- 'get_coating_label',
- 'get_coating_labels_by_type',
- 'get_constants',
- 'get_core_losses_model_information',
- 'get_core_material_names',
- 'get_core_material_names_by_manufacturer',
- 'get_core_material_steinmetz_coefficients',
- 'get_core_materials',
- 'get_core_shape_families',
- 'get_core_shape_names',
- 'get_core_shapes',
- 'get_core_temperature_dependant_parameters',
- 'get_core_temperature_model_information',
- 'get_default_models',
- 'get_equivalent_wire',
- 'get_gap_reluctance_model_information',
- 'get_insulation_material_names',
- 'get_insulation_materials',
- 'get_layers_by_section',
- 'get_layers_by_winding_index',
- 'get_material_data',
- 'get_material_permeability',
- 'get_material_resistivity',
- 'get_outer_dimensions',
- 'get_sections_description_conduction',
- 'get_settings',
- 'get_shape_data',
- 'get_strand_by_standard_name',
- 'get_unique_wire_diameters',
- 'get_wire_coating_by_label',
- 'get_wire_conducting_diameter_by_standard_name',
- 'get_wire_data',
- 'get_wire_data_by_name',
- 'get_wire_data_by_standard_name',
- 'get_wire_material_names',
- 'get_wire_materials',
- 'get_wire_names',
- 'get_wire_outer_diameter_bare_litz',
- 'get_wire_outer_diameter_enamelled_round',
- 'get_wire_outer_diameter_insulated_litz',
- 'get_wire_outer_diameter_insulated_round',
- 'get_wire_outer_diameter_served_litz',
- 'get_wire_outer_height_rectangular',
- 'get_wire_outer_width_rectangular',
- 'get_wires',
- 'load_core_data',
- 'plot_core',
- 'plot_current_density',
- 'plot_field',
- 'plot_layers',
- 'plot_sections',
- 'plot_turns',
- 'plot_wire',
- 'reset_settings',
- 'resolve_dimension_with_tolerance',
- 'scale_waveform_time_to_frequency',
- 'set_settings',
- 'simulate',
- 'wind',
- 'wind_by_layers',
- 'wind_by_sections',
- 'wind_by_turns']


# TODO
create additional documentation sections for:
1. Advanced usage and modeling details
2. Contribution guidelines
3. Development setup
4. Performance optimization tips
5. Troubleshooting guide