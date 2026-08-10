# Physics-Guided Dynamic GNN for 3D-Printed Concrete

This repository provides the implementation of the group-node
physics-guided graph neural network (PGNN) and dynamic model-updating
framework developed for predicting the compressive strength of
3D-printed concrete.

# Repository contents

- "01_Pretrain_Group_Node_PGNN.ipynb"
         - Trains the group-node PGNN using the RILEM TC 304-ADC database.
         - Saves the best pre-trained model based on validation RMSE.

- "02_Dynamic_Update_Group_Node_PGNN.ipynb"
         - Loads the pre-trained group-node PGNN.
         - Evaluates the pre-trained model on the ASU dataset without updating.
         - Uses 20% of the ASU dataset for dynamic model updating.
         - Evaluates the updated model on the remaining 80% of the ASU dataset.

- "pretrained_model/group_node_PGNN_pretrained.pt"
         - Pre-trained group-node PGNN model weights.

- "pretrained_model/preprocessing_scalers.joblib"
         - Input and target standardization parameters used during pre-training.

- "trained_models/group_node_PGNN_dynamic_updated.pt"
         - Group-node PGNN model weights after dynamic updating.

- "example_data/input_data_template.csv"
         - Example template showing the required input-data format.

- "requirements.txt"
         - Python packages required to run the notebooks.

# Model architecture

The group-node PGNN uses:

- Two GraphSAGE layers
- 256-dimensional latent representations
- Dropout rate = 0.10
- AdamW optimizer
- Learning rate = 2 × 10^-3
- Weight decay = 1 × 10^-4
- Batch size = 128
- Validation-RMSE-based early stopping
- Random seed = 42

# Dynamic updating workflow

1. Train the general group-node PGNN using the RILEM database.
2. Save the pre-trained model weights and preprocessing parameters.
3. Load the same pre-trained model for a new dataset.
4. Evaluate the model without updating as a benchmark.
5. Use 20% of the new dataset to update the pre-trained model.
6. Evaluate the updated model using the remaining 80% of the new dataset.

# Installation

Install the required Python packages using:

pip install -r requirements.txt

# Data format

The new dataset should contain the same input variables used during
pre-training. An example is provided in "example_data/input_data_template.csv".

# Citation

If you use this code or the pre-trained model, please cite the associated article:

A Physics-Guided, Dynamic Graph Neural Network Framework to Model the Compressive Strength of 3D-Printed Concrete

Full citation information will be added after publication.
