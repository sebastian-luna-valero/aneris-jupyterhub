FROM quay.io/pangeo/ml-notebook:2025.01.24

# Prevent Python from writing .pyc files and buffering stdout
ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1

# Copy environment file and create conda env
COPY environment.yml .
RUN conda env create -f environment.yml \
    && conda clean -afy
