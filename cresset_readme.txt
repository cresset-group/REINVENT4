The pyproject.toml file has been modified to remove dependencies for libraries that flare-python
already has. openEye has also been removed as it is not required and has licensing issues.
torchvision has been added as it is used by REINVENT but isn't included in our version of torch.

When rebuilding REINVENT, if any changes are required in pyproject.toml, run the following
command to regenerate the requirements file containing all of REINVENT's dependencies:
  pip-compile --output-file=cresset_requirements_<OS>.txt pyproject.toml
The requirements file then needs to be edited to comment out all of the libaries that are not
needed. The existing file can be used for comparison.

To build REINVENT, run the following commands:
  pyflare -m pip install -r cresset_requirements_<OS>.txt
  pyflare -m pip install --no-deps .
Using pyflare to do this means that the REINVENT build matches the libraries that are included
in Flare. The build can be found in build/lib.