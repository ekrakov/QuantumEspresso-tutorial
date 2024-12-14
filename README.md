# QuantumEspresso-tutorial
QE intro for MATSCI 331 
## Getting on  Rice 
To access rice, run 
```bash
ssh <SUNetID>@rice.stanford.edu
```
## Accesing Rice 
Instead of typing this every time, it is easier to alias this command in your bashrc:

```bash
emacs ~/.bashrc
```

```bash
alias rice='ssh <SUNetID>@rice.stanford.edu'
```

To apply these changes, run:

```bash
source ~/.bashrc
```

Now, you can access `rice` by simply typing `rice` in your command line.


## Setup

open your bashrc with your preferred text editor (emacs)

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

First, make a directory to run all calculations related to Si

```bash
mkdir matsci331
cd matsci331
```

Now, lets setup an initial folder for our Si calculations 

```bash
mkdir Si_calcs
cd Si_calcs
```


The inputs for Si are setup already. We will copy them into an initial directory 

```bash
cp -r /afs/ir/users/a/k/akashr/public/matsci331/Si Si_init
cd Si
```

The folder `Si` has 2 important inputs. The pseudopotential file, `Si.pz-vbc.UPF` and the input file for the scf cycle. `si.scf.in`

Take a look at `si.scf.in`

```bash
cat si.scf.in
```

```
&CONTROL
  title = 'Silicon bulk',
  calculation = 'scf',
  restart_mode = 'from_scratch',
  outdir = 'tmp',
  pseudo_dir = './',
  prefix = 'silicon',
  tstress = .true.,
  tprnfor = .true.,
/
&SYSTEM
  ibrav = 2,
  celldm(1) = 11.1,
  nat = 2,
  ntyp = 1,
  ecutwfc = 18.0 ,
/
&ELECTRONS
  conv_thr = 1.0d-8 ,
  mixing_mode = 'plain' ,
  mixing_beta = 0.7 ,
  diagonalization = 'david' ,
/
ATOMIC_SPECIES
   Si   28.08600  Si.pz-vbc.UPF 
ATOMIC_POSITIONS 
   Si      0.000000000    0.000000000    0.000000000    1  1  1 
   Si      0.250000000    0.250000000    0.250000000    1  1  1
K_POINTS automatic
  8 8 8 0 0 0
```

## Run  

In order to run Quantum Espresso type 


```bash
pw.x < si.scf.in | tee si.scf.out
```
in your the command line. Make sure you are in the `Si` folder. Since we exported the path containing `pw.x`, it is no longer necessary to type the entire path. 

The final results are outputted in `si.scf.out`. 

