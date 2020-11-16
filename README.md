# azure-function-librosa
testing libsndfile errors in python azure functions

first run

pip wheel -r requirements.txt -w wheelhouse

then publish to azure with

func azure functionapp publish functionappname --build remote

call function with get from browser to

https://functionappname.azurewebsites.net/api/AzureTest?


trace from azure portal:

Result: Failure Exception: OSError: sndfile library not found Stack: 
File "/azure-functions-host/workers/python/3.8/LINUX/X64/azure_functions_worker/dispatcher.py", line 266, in _handle__function_load_request func = loader.load_function( 
File "/azure-functions-host/workers/python/3.8/LINUX/X64/azure_functions_worker/utils/wrappers.py", line 32, in call return func(*args, **kwargs) 
File "/azure-functions-host/workers/python/3.8/LINUX/X64/azure_functions_worker/loader.py", line 76, in load_function mod = importlib.import_module(fullmodname) 
File "/usr/local/lib/python3.8/importlib/__init__.py", line 127, in import_module return _bootstrap._gcd_import(name[level:], package, level) 
File "<frozen importlib._bootstrap>", line 1014, in _gcd_import File "<frozen importlib._bootstrap>", line 991, in _find_and_load 
File "<frozen importlib._bootstrap>", line 961, in _find_and_load_unlocked 
File "<frozen importlib._bootstrap>", line 219, in _call_with_frames_removed 
File "<frozen importlib._bootstrap>", line 1014, in _gcd_import 
File "<frozen importlib._bootstrap>", line 991, in _find_and_load 
File "<frozen importlib._bootstrap>", line 975, in _find_and_load_unlocked 
File "<frozen importlib._bootstrap>", line 671, in _load_unlocked 
File "<frozen importlib._bootstrap_external>", line 783, in exec_module 
File "<frozen importlib._bootstrap>", line 219, in _call_with_frames_removed 
File "/home/site/wwwroot/AzureTest/__init__.py", line 5, in <module> import librosa 
File "/home/site/wwwroot/.python_packages/lib/site-packages/librosa/__init__.py", line 211, in <module> from . import core 
File "/home/site/wwwroot/.python_packages/lib/site-packages/librosa/core/__init__.py", line 6, in <module> from .audio import * # pylint: disable=wildcard-import 
File "/home/site/wwwroot/.python_packages/lib/site-packages/librosa/core/audio.py", line 8, in <module> import soundfile as sf 
File "/home/site/wwwroot/.python_packages/lib/site-packages/soundfile.py", line 142, in <module> raise OSError('sndfile library not found')
