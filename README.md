# JupyterHub deployment for ANERIS

This repository includes brief documentation and configuration
for the deployment of [JupyterHub](https://jupyter.org/hub) for the 
[ANERIS](https://aneris.eu/) project using the
[Cloud Container Compute](https://www.egi.eu/service/cloud-container-compute/)
service backed by the
[CERIT-SC Kubernetes Container Platform](https://docs.cerit.io/en/docs/platform/overview).

# Work in progress: Getting access via EGI Check-in demo

Until we complete additional agreements the steps to get access
to the JupyterHub deployment are listed below:

1. Create an account in EGI Check-in demo
   by visiting [https://aai-demo.egi.eu/signup](https://aai-demo.egi.eu/signup).

2. Request access using the EGI Check-in account created in step 1) and visiting the
   [enrolment URL](https://aai-demo.egi.eu/auth/realms/id/account/#/enroll?groupPath=/vo.aneris.eu).

3. Access JupyterHub in [https://aneris.vm.fedcloud.eu](https://aneris.vm.fedcloud.eu/).

# GPUs

Access to GPUs is granted via these available environments:
* `quay.io/pangeo/ml-notebook:latest`
* `quay.io/pangeo/pytorch-notebook:latest`

However, since this is a shared environment, availability of GPUs
will depend on current allocation. In case of problems accessing GPUs
please open an
[issue](https://github.com/sebastian-luna-valero/aneris-jupyterhub/issues).

# AIES-MAC

## Initial configuration of AIES-MAC

* Log into [https://aneris.vm.fedcloud.eu/](https://aneris.vm.fedcloud.eu/)
* Use this option from the drop-down menu: `aies-mac:2025-12-15-a`
* Once the environment is ready, use the `Git` menu at the top,
  select `Clone a Repository`,
  and enter `https://gitlab.univ-nantes.fr/paul-gilloteaux-p/aneris_aies-mac.git`
* Go to the folder where you cloned the repo and open
  the notebook of interest; e.g. `aneris_aies-mac/CS1/AIES_MAC_forCS1.ipynb`
* Switch to the conda `env:aneris` kernel

## Update AIES-MAC

* Go to the folder where you cloned the repo; e.g. `aneris_aies-mac/`
* Use the `Git` menu at the top, select `Pull from Remote`

# Known problems

## Error: pod is forbidden: exceeded quota

If you get an error similar to this one:

```bash
Spawn failed: (403) Reason: error HTTP response headers: [...]
"status":"Failure","message":"pods \"jupyter-slunavalero3\" is forbidden: exceeded quota [..]
```

<img width="1206" height="430" alt="aneris-quota-limit" src="https://github.com/user-attachments/assets/fd17d6b9-d9a5-4e3d-8431-85a303cd4c04" />

The issue is that you have hit the quota limit either in CPU or GPU resources.

See this [grafana dashboard](https://kuba-mon-int.cloud.e-infra.cz/d/vd9rFCL4zaneris/aneris).
The cause might be that all GPUs are being used at the moment. Either coordinate among
the users of GPUs or open an issue to discuss the best way forward.
