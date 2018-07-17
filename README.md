# Kubeflow Oscon Demo - Github Issue Summarization

## End-to-End kubeflow tutorial using a Sequence-to-Sequence model

This example demonstrates how you can use `kubeflow` end-to-end to train and
serve a Sequence-to-Sequence model on an existing kubernetes cluster. This
tutorial is based upon @hamelsmu's article ["How To Create Data Products That
Are Magical Using Sequence-to-Sequence
Models"](https://medium.com/@hamelhusain/how-to-create-data-products-that-are-magical-using-sequence-to-sequence-models-703f86a231f8).

By the end of this tutorial, you should learn how to:

*   Spawn up a Jupyter Notebook on the kubeflow cluster
*   Train a Sequence-to-Sequence model using TensorFlow and GPUs on the cluster
  * This is a tutorial on how to summarize text and generate features from Github Issues using deep learning with Keras and TensorFlow.

## Kubeflow cluster

A shared kubeflow cluster has already been setup for the purpose of this tutorial. To install your own kubeflow cluster refer to docs https://www.kubeflow.org/docs/about/kubeflow/

## Access to the kubeflow cluster

Request access to the cluster by providing your Google sign-in email address to Ankush Agarwal (agwl@google.com).

Whitelisting takes ~5 min to take effect. The cluster should be available at `https://kubeflow.endpoints.oscon2018-kubeflow.cloud.goog/hub/`


# Training using Jupyter Notebook on Kubeflow Cluster

## Spawing a Jupyter Notebook.

By this point, you should have a access to JupyterHub at https://kubeflow.endpoints.oscon2018-kubeflow.cloud.goog/hub/

Go to jupyterhub and click on "Start my server". In the Image field, enter : `gcr.io/agwlkubeflow/oscon2018demo-gpu`. In the `Extra Resource Limits`, specify `{"nvidia.com/gpu": 1}`

This ensures that the spawned pod gets 1 GPU.

Other fields are optional and can be left empty. Click on Spawn.

This should spawn a jupyter notebook in a pod and redirect you to it. This should take < 1 minute.

## Download training files

Open the Jupyter Notebook interface and create a new Terminal by clicking on
menu, *New -> Terminal*. In the Terminal, clone this git repo by executing: `

```commandline
git clone https://github.com/ankushagarwal/oscondemo.git
```

Now you should have all the code required to complete training in the `oscondemo/notebooks` folder. Navigate to this folder in jupter notebook tree.
Here you should see two files:

*    `Training.ipynb`
*    `seq2seq_utils.py`

## Perform training

Open the `Training.ipynb` notebook. This contains a complete walk-through of
downloading the training data, preprocessing it, and training it.

Run the `Training.ipynb` notebook, viewing the output at each step to confirm
that the resulting models produce sensible predictions.

## Complete

Congratulations! You have successfully trained a Sequence to Sequence model on a Kubernetes cluster using Kubeflow. Visit https://www.kubeflow.org/ for more info about the project and https://github.com/kubeflow/examples for more examples of using Kubeflow
