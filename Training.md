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

Now you should have all the code required to complete training in the `oscondemo/notebooks` folder. Navigate to this folder.
Here you should see two files:

*    `Training.ipynb`
*    `seq2seq_utils.py`

## Perform training

Open the `Training.ipynb` notebook. This contains a complete walk-through of
downloading the training data, preprocessing it, and training it.

Run the `Training.ipynb` notebook, viewing the output at each step to confirm
that the resulting models produce sensible predictions.
