# keras with AMD GPU (On Windows 10)

## Install plaidml

1. Install keras in your python environment (anaconda, ...)
2. Install plaidml backend for keras: ```pip install -U plaidml-keras```
  * check install: ```pip install plaidml-keras plaidbench```
3. Run Setup: ```plaidml-setup``` 
4. Use it:
  ```
  os.environ["KERAS_BACKEND"] = "plaidml.keras.backend"
  ```
