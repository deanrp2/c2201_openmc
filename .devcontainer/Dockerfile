# Official OpenMC image: OpenMC 0.16.0 + Python API in /openmc_venv,
# plus the NNDC HDF5 cross-section library (ENDF/B-VII.1 based) at /root/nndc_hdf5.
# OPENMC_CROSS_SECTIONS is already set by the base image.
# Pin a version tag so the environment doesn't change mid-semester.
FROM openmc/openmc:v0.16.0

# Jupyter support for VS Code notebooks and plotting
RUN pip install --no-cache-dir ipykernel matplotlib pandas

# --- Optional: use ENDF/B-VIII.0 instead of the bundled NNDC library ---
# Adds roughly 2-3 GB to the image (slower prebuilds, more storage).
# RUN apt-get update && apt-get install -y --no-install-recommends wget xz-utils && \
#     mkdir -p /opt/xs && cd /opt/xs && \
#     wget -q -O endfb80.tar.xz https://anl.box.com/shared/static/uhbxlrx7hvxqw27psymfbhi7bx7s6u6a.xz && \
#     tar -xJf endfb80.tar.xz && rm endfb80.tar.xz
# ENV OPENMC_CROSS_SECTIONS=/opt/xs/endfb-viii.0-hdf5/cross_sections.xml
