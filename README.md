# Kubernetes test job.

If you’re using the cluster for the first time, perform the first-time setup steps given in the next section.

```
nano job.yaml

```

This is a YAML script that will set up your job for Kubernetes. We have provided a template [here](https://github.com/randypausch/kube-test/blob/main/job.yaml). You only need to replace placeholders for username and ID with the appropriate values in lines 9 and 71, specify the correct path to your code in line 92, and name the job in line 5.

```
cd job/

nano run.sh

```

Prepare a bash script to call your code; we have provided a template [here](https://github.com/randypausch/kube-test/blob/main/job/run.sh). This will execute your code and pipe the output to a file; set the correct path in line 11. Line 9 sets up the environment for using the standard tools we have provided - you can use either py36 or py27 or any other conda environment as per your needs.

Submit the job by running 

```

kubectl create -f job.yaml

```

Monitor its status by running 

```

watch kubectl get pods


```


Monitor output by running 

```

tail -F /path/to/output/file


```


In case of errors, view logs by using 

```

kubectl logs pods/<name of pod>

```


Once your job is complete, or you want to submit the same job after receiving an error, run 

```

kubectl delete pods/<name of pod>

```
