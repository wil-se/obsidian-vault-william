---
alias: []
tags: []
---

# Conda
----
Conda is an open-source, cross-platform, language-agnostic package manager and environment management system. It was originally developed to solve difficult package management challenges faced by [[Python3]] data scientists.

## Common commands

### Create env
```bash
conda create -n myenv python=3.9
```

### List envs
```bash
conda env list
```
or
```bash
conda info --envs
```

### Activate env
```bash
conda activate myenv
```

### Deactivate env
```bash
conda deactivate
```

### Remove env
```bash
conda remove --name myenv --all
```

### Export env to file
```bash
conda env export > environment.yml
```

### Import env from file
```bash
conda env create -f environment.yml
```

### List packages
```bash
conda list
```
