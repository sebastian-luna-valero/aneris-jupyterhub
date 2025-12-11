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

In order to test the AIES-MAC pipeline, please follow the steps in
[this discussion](https://github.com/sebastian-luna-valero/aneris-jupyterhub/issues/2#issuecomment-3332920597).
