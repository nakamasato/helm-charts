# mysql-operator

## Values

1. cloudSecretManagerType: `raw` or `gcp`
1. gcpServiceAccount: Only for `cloudSecretManagerType=gcp`. GCP service account for Pod `SA_NAME@PROJECT.iam.gserviceaccount.com`
1. gcpProjectId: Only for `cloudSecretManagerType=gcp`

## Check

You can check the final yaml with `--dry-run`:

```
helm install mysql-operator ./charts/mysql-operator --dry-run --set cloudSecretManagerType=gcp,gcpServiceAccount=${SA_NAME}@${PROJECT}.iam.gserviceaccount.com,gcpProjectId=$PROJECT --namespace mysql-operator
```
