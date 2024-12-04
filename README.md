# QuantumEspresso-tutorial
QE intro for MATSCI 331 

## Setup 

open your bashrc with your preffered text editor (emacs)

```bash
emacs ~/.bashrc
```

Add the following lines 

```bash
export PATH="/afs/ir/users/a/k/akashr/public/matsci331/exec/bin/:$PATH

ml intel
ml load openmpi
```

The first line loads the executables needed to run quantum espresso. We will be using the plane wave code located in `/afs/ir/users/a/k/akashr/public/matsci331/exec/bin/pw.x`. Since we exported this path, we can access this executable by only running `pw.x`.

to apply these changes, run 

```bash
source ~/.bashrc
```
