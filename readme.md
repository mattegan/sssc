SSSC - Super Simple Scheme Compiler
---

---
As the title suggests, this project will (eventually) be a scheme compiler. The first objective is a scheme -> mips assembly compiler. This subproject will be contained in the `/mips` directory.

The second objective is a compiler for a simple computer architecture and assembly language of my design (the HDL for this architecture will eventually be contained in another repository). After this simple computer is created, and a compiler is working, I may merge the two compilers into a compiler with selectable targets. One possible third target is AVR or PIC assembly.

The `/lit` directory contains various readings I've found over the internet that contain information on compiler design and implementation.

---
MIPS
--
To run the generated MIPS code, I'm using [MiSaSiM](http://users.ece.gatech.edu/~scotty/misasim/), which is tool used in some ECE/CS classes at Georgia Tech. I haven't put much research into other options, but it's what I'm most comfortable with. Unfortunately, the download is not an executable, but rather a python launcher script that must be run with python. I recommend creating an executable with something like `py2app` for ease of use.

Before doing so, remove the code in the `Misasim.py` file that checks for updates on every launch (updates are rare anyway), simply remove all of the `__init__` method of the `Manager` class except for the first line of the method: `Self.Run = True`

After this, I simply used `py2app` using a default generated `setup.py` file created by `py2app`.

```
py2applet --make-setup Misasim.py
python setup.py py2app -A
cd dist
open Misasim.app
```

I won't be packaging Misasim within this repository, as I'm not sure of the licensing restrictions