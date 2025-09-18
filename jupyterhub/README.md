# Deployment how-to

These are the steps to deploy
[Jupyterhub](https://jupyter.org/hub)
on the
[CERIT-SC Kubernetes Container Platform](https://docs.cerit.io/en/docs/platform/overview)
for the [ANERIS](https://aneris.eu/) project.

## Assumptions for deployment

This guide assumes that you have:

1. Access to a kubernetes cluster with `kubectl`.
2. [Helm](https://helm.sh/) is installed (i.e. the `helm` command works).
3. Access to configure DNS hostnames (e.g.
   the [EGI Dynamic DNS](https://docs.egi.eu/users/compute/cloud-compute/dynamic-dns/))

## Get a copy of this repository

For example, using `git clone`, and make sure you are in the correct
workding directory:

```bash
cd working/dir/
git clone git@github.com:sebastian-luna-valero/aneris-jupyterhub.git
cd aneris-jupyterhub
```

## Before going ahead

Please configure the values below accordingly:

* [jupyterhub-secrets.yaml](./jupyterhub-secrets.yaml): `secretToken` must be
  replaced with a hash generated using `openssl rand -hex 32` on Linux.
  Pay also attention to the comments in the file requesting further updates.
* [jupyterhub.yaml](./jupyterhub.yaml): `aneris.vm.fedcloud.eu` must be replaced
  with your DNS hostname.

## Steps

Use `helm` to install **JupyterHub** with the command below:

```bash
helm upgrade jupyterhub jupyterhub/jupyterhub \
  --wait --install \
  --cleanup-on-fail \
  --create-namespace \
  --namespace vo-aneris-eu \
  --version=3.3.8 \
  --values aneris/jupyterhub.yaml \
  --values aneris/jupyterhub-secrets.yaml
```

All going well **JupyterHub** will be available at [https://aneris.vm.fedcloud.eu](https://aneris.vm.fedcloud.eu).
