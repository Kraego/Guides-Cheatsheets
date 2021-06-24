# keras with AMD GPU (On Windows 10)

## Install plaidml

1. Install keras in your python environment (anaconda, ...)
2. Install plaidml backend for keras: ```pip install -U plaidml-keras```
  * check install: ```pip install plaidml-keras plaidbench```
3. Run Setup: ```plaidml-setup```
  * select your gpu in the setup (something like: opencl_amd_gfx ..., maybe you have to use experimental mode)
5. Use it:
  ```
  os.environ["KERAS_BACKEND"] = "plaidml.keras.backend"
  ```
