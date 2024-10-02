# [mysql-operator](https://github.com/nakamasato/mysql-operator)

## Values

1. **adminUserSecretType**: `raw`, `gcp` or `k8s` . With `raw`, you need to give root user password in `MySQL` custom resource. With `gcp`, you can securely store root user password in GCP SecretManager. This root user password is used to manage (create/edit/update) MySQL users, databases, etc. With k8s you need to create (in the same namespace where this operator is installed) two kubernetes secrets one for the root username and another one for root password.
1. **gcpServiceAccount**: Only for `adminUserSecretType=gcp`. GCP service account for Pod `SA_NAME@PROJECT.iam.gserviceaccount.com`
    1. This service account needs the following roles:
        1. `roles/secretmanager.secretAccessor` to allow to get root password from SecretManager
1. **gcpProjectId**: Only for `adminUserSecretType=gcp`
1. **adminUserSecretNamespace**: Only for `adminUserSecretType=k8s`. Kubernetes Namespace of Secret for MySQL admin user credentials.
1. **cloudSQL.instanceConnectionName**: `InstanceConnectionName` for [Google Cloud SQL](https://cloud.google.com/sql/) if you use Cloud SQL to manage with mysql-operator. `<project-id>:<region>:<instance-name>`



## Usage

### Dryrun

You can check the final yaml with `--dry-run`:

```
helm install mysql-operator ./charts/mysql-operator \
    --dry-run \
    --set adminUserSecretType=gcp \
    --set gcpServiceAccount=${SA_NAME}@${PROJECT}.iam.gserviceaccount.com \
    --set gcpProjectId=$PROJECT \
    --set cloudSQL.instanceConnectionName=$PROJECT:$REGION:$INSTANCE_NAME \
    --namespace mysql-operator
```

### Install

```
helm install mysql-operator ./charts/mysql-operator \
    --set adminUserSecretType=gcp \
    --set gcpServiceAccount=${SA_NAME}@${PROJECT}.iam.gserviceaccount.com \
    --set gcpProjectId=$PROJECT \
    --set cloudSQL.instanceConnectionName=$PROJECT:$REGION:$INSTANCE_NAME \
    --namespace mysql-operator
```
