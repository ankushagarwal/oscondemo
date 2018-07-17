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
*   Serve the model using [Seldon Core](https://github.com/SeldonIO/seldon-core/) on a kubernetes cluster.
*   Query the model from a simple front-end application

## Access to the kubeflow cluster

Request access to the cluster by providing your Google sign-in email address to Ankush Agarwal (agwl@google.com). Whitelisting takes ~5 min to take effect. The cluster should be available at `https://kubeflow.endpoints.oscon2018-kubeflow.cloud.goog/hub/`

## Training

See [Training](Training.md)

## Model Serving

See [Model Serving](Serving.md)

## UI

See [UI](UI.md)
