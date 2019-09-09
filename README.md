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


```

