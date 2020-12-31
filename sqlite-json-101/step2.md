If we want to load our data, we need to have a list of all the files we want to load.

Let's search for all the files in our data directory that end in `.json`.

```
from pathlib import Path

files = list(Path("data").glob('**/*.json'))
```{{execute}}

Then we can make a list of all the files we found, without the `.json` extension.
```
filenames = [f.stem for f in files]

print(filenames)
```{{execute}}