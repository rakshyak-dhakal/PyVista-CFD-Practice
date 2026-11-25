# PyVista CFD Data Practice

## Overview
This project explores how to read, inspect, visualize, and convert CFD simulation data using PyVista and NumPy.

The dataset used is PyVista's Electronics Cooling example.

## Dataset Information

The downloaded dataset is a MultiBlock containing two parts:

| Dataset | Type | Points | Cells |
|---|---|---:|---:|
| Structure | PolyData | 187,992 | 344,270 |
| Air | UnstructuredGrid | 610,176 | 1,749,992 |

The air mesh contains fields such as temperature (T), pressure (p), velocity (U), turbulent kinetic energy (k), and other flow variables.

Velocity magnitude was calculated from the three velocity components.

## Work Completed

1. Loaded and inspected the simulation datasets.
2. Printed mesh information and examined point and cell arrays.
3. Checked field shapes, minimum and maximum values, and estimated units.
4. Visualized temperature and velocity magnitude.
5. Created a middle-plane slice at Z = 0.019 m.
6. Clipped half of the air mesh at X = 0.075 m.
7. Converted cell data to point data and compared the results.
8. Created a `load_case(path)` function to extract coordinates and point-data fields.
9. Saved the extracted data in NumPy format and checked the reloaded arrays.

## Files

- `PyVista_CFD_Practice.ipynb` – Notebook containing the complete workflow and outputs.
- `air_mesh.vtu` – Saved air-domain mesh.
- `air_case_data.npz` – Coordinates and extracted field arrays.
- `temperature_distribution.png` – Temperature visualization.
- `velocity_magnitude.png` – Velocity magnitude visualization.

## Data Conversion

The `load_case(path)` function returns a dictionary containing:

- `coords`: Point coordinates with shape (610176, 3).
- One NumPy array for each point-data field.
- Velocity magnitude derived from the velocity vector.

The extracted arrays were saved using `np.savez()` and reloaded successfully. All checked arrays matched their original values.

## What I Learned

- A mesh can contain both point data and cell data, even with the same field names.
- Velocity is a vector with three components, while velocity magnitude is a scalar.
- Slicing and clipping help inspect different regions of a CFD domain.
- Converting cell data to point data interpolates values, so the resulting values can differ even when the plots look similar.
- NumPy arrays provide a convenient format for storing simulation data for later analysis or model training.
