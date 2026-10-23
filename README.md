# tb3py - Python Wrapper for ThreeBodyTB.jl

This package is a simple python wrapper for
[ThreeBodyTB.jl](https://github.com/usnistgov/ThreeBodyTB.jl) that
makes installing and using the code within python easier. It is not
necessary to understand any Julia, and you get full access to the
code.

ThreeBodyTB.jl (see https://github.com/usnistgov/ThreeBodyTB.jl) is a
Julia package to perform tight binding calculations. It is based on
the method described in
[PhysRevMaterials.7.044603](https://journals.aps.org/prmaterials/abstract/10.1103/PhysRevMaterials.7.044603).

<img align="right" src="https://github.com/kfgarrity/ThreeBodyTB.jl/blob/main/docs/src/assets/logo.svg" alt="logo" width="200" >

# Usage

The [documentation](https://pages.nist.gov/ThreeBodyTB.jl/) for
ThreeBodyTB.jl covers detailed usage of the main code. The python
wrapper can access any function from ThreeBodyTB.jl by prepending
`tb3.jl.` for exported functions or by replacing `ThreeBodyTB.jl` for
non-exported functions. For example, the Julia function `makecrys` can
be accessed as follows:

```
>>> import tb3py_test as tb3
>>> c = tb3py_test.jl.makecrys("POSCAR_example")
>>> c = tb3.jl.makecrys("POSCAR_example")
>>> c
Julia:
Units: Å

A1=     5.00000  5.00000  0.00000
A2=     5.00000  0.00000  5.00000
A3=     0.00000  5.00000  5.00000

Si   0.00000  0.00000  0.00000
Si   0.25000  0.25000  0.25000

>>>
```

and an energy calculation and band structure calculation can be
performed as

```
>>> en, tbc, flag = tb3.jl.scf_energy(c)
>>> tb3.jl.plot_bandstr_dos(tbc)
>>> tb3.jl.savefig("t.pdf")
```
which will produce output like

<img align="left" src="t.png" alt="logo" width="600" >\

Basically, you need to write `tb3.jl.` before normal commands. A tutorial is available [here](https://pages.nist.gov/ThreeBodyTB.jl/ug_run/#Running-tight-binding-calculations)

# Installation

To install, clone the repository and run the 

```
git clone git@github.com:kfgarrity/tb3py_test.git
cd tb3py_test
pip install -e .
export JULIA_NUM_THREADS=1
export PYTHON_JULIACALL_HANDLE_SIGNALS=yes
```

The two environment variables are to prevent issues with multithreading between python and julia.



kevin.garrity@nist.gov
Kevin F. Garrity 
Material Data Division: 641.03
Material Measurement Laboratory
National Institute of Standards and Techonology (NIST)
Gaitherburg, MD
