### pdb
---
https://pypi.org/project/pdbpp/
https://github.com/pdbpp/pdbpp


https://pypi.org/project/ipdb/
https://github.com/gotcha/ipdb

```py
// _pdbpp_path_hack/pdb.py
import os

if int(os.environ.get('PDBPP_HIJACK_PDB', 1)):
  pdb_path = os.path.join(os.path.dirname(os.path.dirname(__file__)), 'pdb.py')
else:
  import code
  
  pdb_path = os.path.join(os.path.dirname(code.__file__), 'pdb.py')

with open(pdb_path) as f:
  exec(compile(f.read(), pdb_path, 'exec'))

```

```
```

```py
// ipdb/stdout.py

def update_stout():
  io.stdout = sys.stdout = sys.__stdout__
  
def sset_trace(frame=None, context=3):
  update_stdout()
  if frame is None:
    frame = sys._getframe().f_back
  set_trace(frame, context)
  
def spot_mortem(tb=None):
  update_stdout()
  post_mortem(tb)
  
def spm():
  spot_mortem(sys.last_traceback)
  
@contextmanager
def slaunch_ipdb_on_exception():
  try:
    yield
  except Exception:
    e, m, tb = sys.exc_info()
    print(m.__repr__(), file=sys.stderr)
    spot_mortem(tb)
  finally:
    pass

```

