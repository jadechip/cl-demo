
### Upload DAGs

### Step 1

Create GCS bucket

### Step 2

Create Cloud Composer environment

```bash
export ENVIRONMENT_NAME=ethereum-etl-0
gcloud composer environments create $ENVIRONMENT_NAME --location=us-central1 --zone=us-central1-a \
    --disk-size=100GB --machine-type=n1-standard-4 --node-count=3 --python-version=3 --image-version=composer-1.8.3-airflow-1.10.3 \
    --network=default --subnetwork=default

gcloud composer environments update $ENVIRONMENT_NAME --location=us-central1 --update-pypi-package=ethereum-etl==1.7.0

```

### Step 3

Upload dags

```bash
> ./upload_dags.sh <airflow_bucket>
```

### Citation

Adapted from: https://github.com/blockchain-etl/ethereum-etl-airflow/tree/master/dags