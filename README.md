# helm-charts

## Usage

1. Add or update a Helm chart: push your source code of Helm chart under `charts/<your chart>`
1. New release will be created by [GitHub Actions](https://github.com/nakamasato/helm-charts/blob/main/.github/workflows/release.yaml) (e.g. https://github.com/nakamasato/helm-charts/releases/tag/mysql-operator-0.1.0)
1. Add this helm chart repo to your helm client configuration
    ```
    helm repo add nakamasato https://nakamasato.github.io/helm-charts
    helm repo update
    ```
1. Update repo and search
    ```
    helm search repo nakamasato
    NAME                     	CHART VERSION	APP VERSION	DESCRIPTION
    nakamasato/helm-example  	0.1.0        	v0.0.1     	Simple API application.
    nakamasato/mysql-operator	0.1.0        	v0.2.0     	A Helm chart for Kubernetes
    ```
1. Install
    ```
    helm install example-from-my-repo nakamasato/helm-example
    ```
1. Upgrade (optional)
    ```
    helm upgrade example-from-my-repo nakamasato/helm-example --set xxx=aaa
    ```
1. Uninstall
    ```
    helm uninstall example-from-my-repo
    ```

## Setup

follow [chart-releaser Action](https://github.com/marketplace/actions/helm-chart-releaser#pre-requisites)
