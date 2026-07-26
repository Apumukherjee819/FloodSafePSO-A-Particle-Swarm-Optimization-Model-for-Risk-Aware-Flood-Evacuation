# FloodSafePSO-A-Particle-Swarm-Optimization-Model-for-Risk-Aware-Flood-Evacuation

**FloodSafePSO** is a prototype decision-support system for risk-aware flood evacuation. It uses flood-risk indicators and Particle Swarm Optimization (PSO) to identify routes that balance travel cost, flood-risk exposure, and movement toward safer, higher-elevation locations.

> This is a research and educational prototype. It must not be used for live evacuation decisions without local validation, real-time data, and authorization from disaster-management authorities.

## Project objectives

- Calculate a composite flood-risk score from environmental and demographic variables.
- Classify locations as low, medium, or high flood risk.
- Create a grid-based spatial network for evacuation planning.
- Identify safer evacuation destinations using risk and elevation information.
- Use PSO to search for risk-aware evacuation routes.
- Present results through 3D network, risk, and route visualizations.

## Model overview

The workflow is:

```text
Flood-risk data -> Risk scoring -> Grid network -> Safe-zone selection -> PSO route optimization -> 3D visualization
```

The model combines normalized rainfall, river discharge, water level, and population density with inverted elevation and infrastructure measures:

```text
Risk score = 0.70 x risk component + 0.30 x safety component
```

Candidate routes are assessed using travel time, risk exposure, and positive elevation gain:

```text
Fitness = 1 / (1 + 0.10 x travel_time + 0.05 x risk_exposure - 0.01 x elevation_gain)
```

## Data source

The project uses the **Flood Risk in India** dataset published on Kaggle by `s3programmer`:

- https://www.kaggle.com/datasets/s3programmer/flood-risk-in-india

The reported project run uses 10,000 observations and considers latitude, longitude, rainfall, river discharge, water level, population density, elevation, infrastructure, and flood occurrence.

## Reported prototype configuration

| Item | Value |
|---|---:|
| Spatial grid | 10 x 10 |
| Network nodes | 100 |
| Directed edges | 684 |
| Safe zones | 5 |
| PSO swarm size | 40 particles |
| PSO iterations | 100 |
| Reported best fitness | 176.0016 |
| Reported route length | 9 nodes |

## Requirements

Install the Python packages required by the model:

```bash
pip install pandas numpy matplotlib scipy scikit-learn
```

## Running the model

1. Download the Kaggle dataset and place the CSV file in the project directory.
2. Update the dataset path in `Advanced_PSO_Evacuation_Model_3D.py` if needed.
3. Run the model:

```bash
python Advanced_PSO_Evacuation_Model_3D.py
```

## Generated outputs

The model produces the following analytical figures:

- `01_3D_Flood_Risk_Surface.png` - spatial flood-risk surface.
- `02_3D_Evacuation_Network.png` - grid network and five safe zones.
- `03_Evacuation_Analysis.png` - risk distribution and variable relationships.
- `04_3D_Optimal_Route.png` - PSO-selected evacuation route.

This workspace also includes:

- `outputs/PSO_Flood_Evacuation_Project_Report.docx` - comprehensive project report.
- `outputs/flood_risk_category_distribution.png` - report-ready risk-category chart.

## Limitations

- The network is a coarse grid, not a real road network.
- The prototype does not include live rainfall, flood depth, road closures, traffic, or shelter capacity.
- A PSO route must be checked for geographic and road feasibility before any operational use.
- Reported outputs are demonstration results and should be repeated across multiple random seeds for stability analysis.

## Future improvements

- Integrate GIS road networks, bridge conditions, and real-time closures.
- Add live weather, gauge, satellite, and flood-extent data.
- Include shelter capacity, vulnerable populations, and traffic constraints.
- Compare PSO against Dijkstra, A*, genetic algorithms, and other routing methods.
- Validate the model using historical flood and evacuation records.

## License and attribution

Please follow the Kaggle dataset's license and attribution requirements when using or distributing the data.
