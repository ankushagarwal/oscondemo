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
*   Serve the model using [Seldon Core](https://github.com/SeldonIO/seldon-core/)
*   Query the model from a simple front-end application

## Access to the kubeflow cluster

Request access to the cluster by providing your Google sign-in email address to Ankush Agarwal (agwl@google.com). Whitelisting takes ~5 min to take effect. The cluster should be available at `https://kubeflow.endpoints.oscon2018-kubeflow.cloud.goog/hub/`

## Spawing a Jupyter Notebook.

By this point, you should have a access to JupyterHub at https://kubeflow.endpoints.oscon2018-kubeflow.cloud.goog/hub/

Go to jupyterhub and click on "Start my server". In the Image field, enter : `gcr.io/kubeflow-images-public/tensorflow-1.8.0-notebook-cpu:v0.2.1`

Other fields are optional and can be left empty. Click on Spawn.

This should spawn a jupyter notebook in a pod and redirect you to it. This should take < 1 minute.

## Download training files

Open the Jupyter Notebook interface and create a new Terminal by clicking on
menu, *New -> Terminal*. In the Terminal, clone this git repo by executing: `

```commandline
git clone https://github.com/ankushagarwal/oscondemo.git
```

Now you should have all the code required to complete training in the `oscondemo/notebooks` folder. Navigate to this folder.
Here you should see two files:

*    `Training.ipynb`
*    `seq2seq_utils.py`

## Perform training

Open the `Training.ipynb` notebook. This contains a complete walk-through of
downloading the training data, preprocessing it, and training it.

Run the `Training.ipynb` notebook, viewing the output at each step to confirm
that the resulting models produce sensible predictions.

## Export trained model files

After training completes, download the resulting files to your local machine.
The following files are needed for serving results:

* `seq2seq_model_tutorial.h5` - the keras model
* `body_pp.dpkl` - the serialized body preprocessor
* `title_pp.dpkl` - the serialized title preprocessor

If you haven't already, clone the [kubeflow/examples](https://github.com/kubeflow/examples) repo locally, then issue the following commands to place these three files into the `github_issue_summarization/notebooks` folder on your local machine:

```
cd github_issue_summarization/notebooks
PODNAME=`kubectl get pods --namespace=${NAMESPACE} --selector="app=jupyterhub" --output=template --template="{{with index .items 0}}{{.metadata.name}}{{end}}"`
kubectl --namespace=${NAMESPACE} cp ${PODNAME}:/home/jovyan/examples/github_issue_summarization/notebooks/seq2seq_model_tutorial.h5 .
kubectl --namespace=${NAMESPACE} cp ${PODNAME}:/home/jovyan/examples/github_issue_summarization/notebooks/body_pp.dpkl .
kubectl --namespace=${NAMESPACE} cp ${PODNAME}:/home/jovyan/examples/github_issue_summarization/notebooks/title_pp.dpkl .
```

For information on:
- [Training the model using TFJob](02_training_model_tfjob.md)
- [Distributed training using tensor2tensor](02_tensor2tensor_training.md)
