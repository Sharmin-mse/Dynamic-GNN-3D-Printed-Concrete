# Dynamic GNN for 3D-Printed Concrete

This repository contains the Python codes and trained models developed for predicting the compressive strength of 3D-printed concrete using a physics-guided graph neural network (PGNN).

The model was initially trained using the RILEM experimental database. A dynamic GNN approach was then developed to allow researchers to update the pretrained model using their own experimental data.

## What is included?

- **Step 1_Pretrained_Group_Node_PGNN.ipynb:** Code used to train the original PGNN model using the RILEM dataset.
- **Step 2_Dynamic_Group_Node_PGNN.ipynb:** Code for updating the pretrained model using a new experimental dataset and comparing predictions before and after updating.
- **group_node_PGNN_pretrained.pt:** Saved pretrained model.
- **group_node_PGNN_scalers.joblib:** Saved data scalers required to use the pretrained model.
- **group_node_PGNN_dynamic_updated.pt:** Model saved after updating with the ASU experimental dataset.
- **input_data_template.csv:** Example showing the required input variables and data format.

The three saved model files are located in the `trained_models` folder.

## How can other researchers use this model?

Researchers can use the pretrained PGNN model with their own experimental data without repeating the original training process or obtaining the RILEM database.

To do this, prepare a dataset containing the same 17 input variables and measured compressive strength, following the provided template. Save it as an Excel file, update the data file path in **Step 2**, and run the notebook.

The notebook uses 20% of the new experimental data to update the pretrained model and evaluates its performance on the remaining 80%.

This framework allows researchers to adapt an existing model to their own materials and printing conditions without developing a new model from scratch.

# Citation
If you use this work, please cite "A Physics-Guided, Dynamic Graph Neural Network Framework to Model the Compressive Strength of 3D-Printed Concrete".
