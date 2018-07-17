# Prerequisite

* glcoud cli
* kubectl cli

Run gcloud init and sign in with your google credentials.

# Get cluster credentials

```
gcloud container clusters get-credentials kubeflow --zone us-central1-a --project oscon2018-kubeflow
```

Ensure that you can run `kubectl get pods -nkubeflow`


# Running a Tensorflow Distributed Training job

Edit the [tfjob.yaml](tfjob.yaml) file locally and add a name to the job. This name should be unique to you. You can use your `{username}-job` for the name of the job. Example: "ankushagarwal-job".

To submit the job, you can run

```
kubectl apply -f tfjob.yaml
```

This should create a tensorflow distributed training job on the cluster.

You can look at the running jobs by running: `kubectl get tfjobs -nkubeflow`

You can look at the pods by running: `kubectl get pods -nkubeflow -ltf_job_key={job-name}`

Here job-name is the name that you used in the previous step for defining the job.

You can look at the logs of the pod by running `kubectl logs -nkubeflow {pod_name}`
