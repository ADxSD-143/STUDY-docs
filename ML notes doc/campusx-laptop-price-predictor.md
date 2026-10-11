# CampusX Laptop Price Predictor — Project Study Notes

**Source repository:** [campusx-official/laptop-price-predictor-regression-project](https://github.com/campusx-official/laptop-price-predictor-regression-project)

These notes are for understanding and learning from the existing project before attempting to containerize it. Keep the source project intact and make Docker experiments in your own local clone/branch.

## Files confirmed in the repository

- `laptop_data.csv` — dataset.
- `laptop-price-predictor.ipynb` — data analysis, feature engineering and model workflow.
- `app.py` — Streamlit prediction UI.
- `df.pkl` — serialized dataframe used by the UI.
- `pipe.pkl` — serialized preprocessing/model pipeline used for predictions.
- `requirements.txt` — lists `streamlit` and `sklearn`.
- `Procfile` and `setup.sh` — deployment-related files.

## How the app works

1. `app.py` loads the serialized pipeline and dataframe via Python pickle.
2. Streamlit input widgets collect brand, laptop type, RAM, weight, touchscreen, IPS panel, screen size, resolution, CPU, HDD, SSD, GPU, and OS.
3. The app converts touchscreen and IPS values to 0/1, calculates PPI from resolution and screen size, and creates a 12-feature prediction input.
4. The pipeline predicts a log-price; the app exponentiates the result and displays the predicted price.

## Dependency note

The app imports NumPy, but the checked-in `requirements.txt` lists only `streamlit` and `sklearn`. Verify the environment from a clean install rather than assuming all dependencies are declared. The app also loads pickle artifacts; only load pickle files from a trusted source because deserialization can execute code.

## Study checklist

- [ ] Read `app.py` from top to bottom.
- [ ] Understand what the dataframe and model pipeline artifacts are used for.
- [ ] Run the app locally.
- [ ] Make one prediction and verify the interface.
- [ ] Inspect the notebook's preprocessing/model pipeline.
- [ ] Identify the app's runtime command and port.
- [ ] Only then begin the Dockerfile experiment.

## Docker learning extension

In your own clone, add a Dockerfile, install verified dependencies, and start Streamlit bound to `0.0.0.0`. Publish the container port to localhost and test one prediction. Do not copy local virtual environments or secrets into the image.

Docker packages an app's runtime; a successful container build does not prove model accuracy. Evaluate model quality separately.
