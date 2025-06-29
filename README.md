
# CSDevRepo


# SNHU CS-340: Grazioso Salvare Dashboard

## About the Project / Project Title

The **Grazioso Salvare Dashboard** is a data visualization and interaction platform built using Plotly Dash in Python. It allows the user to filter and analyze animal shelter data from the Austin Animal Center via a MongoDB backend. This dashboard was developed as part of the CS-340 Software Development course at Southern New Hampshire University (SNHU).

The dashboard is designed specifically for **Grazioso Salvare**, a company specializing in training rescue dogs, to help identify dogs best suited for specific types of rescue operations based on breed, age, and sex.

## Motivation

This project was developed to:
- Provide an intuitive and professional interface for Grazioso Salvare to search and filter available dogs for training.
- Demonstrate full-stack software development using Python, Dash, and MongoDB.
- Apply CRUD functionality through callbacks, filtering, and data visualizations.

## Getting Started

To run the dashboard locally, you’ll need to ensure the following dependencies are installed:

- Python 3.9 - Can be installed via [https://www.python.org/](https://www.python.org/)
- MongoDB - Installed via [https://www.mongodb.com/docs/manual/installation/](https://www.mongodb.com/docs/manual/installation/) or using a virtual machine with it pre-installed
- PyMongo - Installed via `pip install pymongo`
- Dash Reference in Jupyter via `import dash_leaflet as dl` and it's other dependencies
- Plotly Imported in jupyter notebook as `import ploty.express as px`
- Pandas Imported into jupyter notebook as `import pandas as pd`
- NumPy Imported into jupyter notebook as `pandas as pd`
- JupyterDash - Installed via `pip install jupyterlab` [https://jupyter.org/install](https://jupyter.org/install) 
- A running MongoDB instance with animal outcome data

You should also have the following files and resources:
- `animal_shelter.py` (CRUD Python module from Project One)
- `grazioso.png` (logo image)
- Access to the `aacuser` MongoDB credentials

## Installation

1. **Clone or download the repository.**
2. Install dependencies:
    ```bash
    pip install dash dash-leaflet jupyter-dash plotly pandas numpy
    ```
3. Ensure `animal_shelter.py` is in your project directory and correctly configured.
4. Place the `grazioso.png` logo in the working directory.

## Usage

### Running the Dashboard

Once setup is complete

1. Launch the Jupyter Notebook or run the `.py` file:
    ```bash
    jupyter notebook
    ```
2. Open the `ProjectTwoDashboard.ipynb` file.
3. Execute the cells to start the dashboard.
4. The dashboard will appear within the Jupyter environment.

### Key Features

- **Interactive Filtering Options**
    - Users can select from:
        - Water Rescue
        - Mountain Rescue
        - Disaster Rescue
        - Reset to show all

    - Each selection dynamically updates the:
        - Data Table
        - Pie Chart
        - Geolocation Map
        
## Code Example

The following snippet shows how the dashboard dynamically filters dogs for disaster rescue using MongoDB queries:

```python
def apply_filter(filter_type):
    if filter_type == "disaster":
        return shelter.read({
            "animal_type": "Dog",
            "breed": {"$in": [
                "Doberman Pinscher", "German Shepherd", 
                "Golden Retriever", "Bloodhound", "Rottweiler"
            ]},
            "sex_upon_outcome": "Intact Male",
            "age_upon_outcome_in_weeks": {"$gte": 20, "$lte": 300}
        })
```


- **Dashboard Widgets**
    - [ ] **Screenshot of dashboard filtered to display Water Rescue dogs**
    ![](https://i.gyazo.com/4777ead93ae47ffa40214e29dd8bceda.png)
    - [ ] **Screenshot of dashboard filtered to display Mountain Rescue dogs**
 ![](https://i.gyazo.com/103b5ee058ca681447aff89223bcb8ca.png)
    - [ ] **Screenshot of dashboard filtered to display Disaster Rescue dogs**
![](https://i.gyazo.com/ad3461f65adb89e345fa32b5023113bb.png)
    - [ ]   **Screenshot of the unfiltered, Reset View**![](https://i.gyazo.com/70dcaa3c7f8bb85b022258f122f757b3.png)

- **Geolocation Map**
    - Displays a marker on the map based on the selected dog's location
    - ![](https://i.gyazo.com/6b768e1f3c765b0645d7afe717e23b83.png)

- **Pie Chart**
    - Displays the top 5 breeds for the currently filtered dataset
    
**This figure is the pie chart distribution for the unfiltered dataset**
    - ![](https://i.gyazo.com/4b1e215cff01ca812fe478bcdf71db82.png)

## Tests

The following were tested & verified to work as expected:

- CRUD queries return correct entries for each filter (based on age, sex, and breed)
- Filters dynamically update the table, pie chart, and map
- Dashboard runs without error in JupyterDash
- Logo loads and redirects properly

Manual user testing was used to verify the functionality of all filters and interactions across different datasets.
```python 
 #Verify table updates with water rescue filter
records = apply_filter('water')
assert len(records) > 0  # Ensure results return for valid breeds and age
```

## Contact

**Tucker Middleton**  
GitHub: https://github.com/Tucks-dev
Course: CS-340 – Software Development  
Institution: Southern New Hampshire University  
