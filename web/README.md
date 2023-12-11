**Instructions**
- Create a virtual environment (optional but recommended):
    python -m venv venv
    source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
- Install the Requirements: pip install -r requirement.txt
>:bulb:
if you ran into problems installing requirements.txt on ubuntu , or if you got this error :
```shell
× Building wheel for pycairo (pyproject.toml) did not run successfully.                                   
  │ exit code: 1                                                                                            
  ╰─> [15 lines of output]                                                                                  
      running bdist_wheel                                                                                   
      running build                                                                                         
      running build_py                                                                                      
      creating build                                                                                        
      creating build/lib.linux-x86_64-cpython-38                                                            
      creating build/lib.linux-x86_64-cpython-38/cairo                                                      
      copying cairo/__init__.py -> build/lib.linux-x86_64-cpython-38/cairo                                  
      copying cairo/__init__.pyi -> build/lib.linux-x86_64-cpython-38/cairo                                 
      copying cairo/py.typed -> build/lib.linux-x86_64-cpython-38/cairo                                     
      running build_ext                                                                                     
      Package cairo was not found in the pkg-config search path.                                            
      Perhaps you should add the directory containing `cairo.pc'                                            
      to the PKG_CONFIG_PATH environment variable
      No package 'cairo' found
      Command '['pkg-config', '--print-errors', '--exists', 'cairo >= 1.15.10']' returned non-zero exit stat
us 1.
      [end of output]
```
>:bulb:
try installing those missing dependencies
```shell
sudo apt install libcairo2-dev pkg-config python3-dev
```


- Then, make database migrations:
```shell
python manage.py makemigrations
```
```shell
python manage.py migrate
```
- And finally, run the application: 
```shell
python manage.py runserver
```


For Admin Account, please create one with superuser!

# Application usage notes
- contact numbers should match this regex pattern `[6789][0-9]{9}`
example phone/contact numbers are
`9876543210`