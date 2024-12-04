# QuantumEspresso-tutorial
QE intro for MATSCI 331 
## Getting on to Rice 
To access rice, run 
```bash
ssh <SUNetID>@rice.stanford.edu
```

Instead of typing this every time, it is easier to alias this command in your bashrc 

```bash
emacs ~/.bashrc
```

```bash
alias rice='ssh <SUNetID>@rice.stanford.edu'                                                                                          
```
to apply these changes, run 

```bash
source ~/.bashrc
```

Now, you can access rice by by simply typing `rice` in your command line. 

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
Now that this is set up, lets get the files we need to run caluclations for Si.

First, make a directory to run all these calculations

```bash
mkdir matsci331
cd matsci331
```

The inputs for Si are setup already :). To get them, run 

```
cp -r /afs/ir/users/a/k/akashr/public/matsci331/Si ./
cd Si
```




