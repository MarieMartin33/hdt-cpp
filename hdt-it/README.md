# HDT-it! GUI tool for the HDT triple format

Overview
=================

HDT-it is a tool that can generate
and consume RDF files in HDT format. It demonstrates the capabilities
of HDT by allowing to search basic triple patterns against HDT files, and
also visualizes the 3D adjacency matrix of the underlying RDF graph to
provide an overview of the dataset distribution.

Download executable
=================

An executable version of the tool is available for multiple platforms in http://www.rdfhdt.org/downloads/ 

Compiling (MacOS Sonoma 14.3)
=================

Install and check dependencies: 

- Qt5
- automake, autoconf, pkg-config...
- python3, meson, ninja
- serd

```sh
    $ brew install python
    $ brew install autoconf
    $ brew install libtool
    $ brew install pkg-config
    $ brew install aclocal
    $ brew install cloc
    $ brew install automake
```

```sh
    $ # verify Qt version:
    $ qmake --version
    $ # this installs Qt6 by default. this won't work later at compilation time:
    $ # brew install qt
    $ # this installs Qt5:
    $ brew install qt5
    $ # this forces qt5 symlink if Qt6 was installed. Check before apply:
    $ brew link --overwrite qt@5 --dry-run
    $ brew link qt5 --force
    $ brew link --overwrite qt@5
```

Compile:

(in case of pb: run "make clean" and resubmit yours commands)
	
1.Compile a static version of the "serd" library:

```sh
    $ git clone https://github.com/drobilla/serd.git
    $ cd serd

    $ python3 -m venv .venv
    $ source .venv/bin/activate
    $ python3 -m pip install meson
    $ python3 -m pip install ninja
    $ meson setup --default-library=static build
    $ cd buid
    $ meson configure
    $ meson compile
    $ meson install
    $ ls -al /usr/local/lib/
    $ deactivate
```

2. Execute Qmake in libcds:

```sh
    $ cd libcds
    $ qmake 
    $ make
    $ sudo make install
    $ ls -al /usr/local/lib/
```

3.Execute Qmake in libhdt:

```sh
    $ cd libhdt
    $ qmake
    $ # To compile the library run `make`, this will generate the library and tools:
    $ make
    $ sudo make install
    $ ls -al /usr/local/lib/
```

4.Execute Qmake in hdt-it:

```sh
    $ cd hdt-it
    $ ./autogen.sh
    $ ./configure
    $ make -j2
    $ sudo make install
    $ ls -al /usr/local/lib/
```

The application should be available in a new hdt-it subfolder (e.g. hdt-it/unix, hdt-it/win32, hdt-it/macx)

5. Launch the HDT-IT Gui application:

```sh
    $ # under MacOSX:
    $ cd hdt-it/macx/HDT-it.app/Contents/Resources
    $ ./HDT-it
```
 
Licensing
=================
Copyright (C) 2012, Mario Arias, Javier D. Fernandez, Miguel A. Martinez-Prieto
All rights reserved.

This library is free software; you can redistribute it and/or
modify it under the terms of the GNU Lesser General Public
License as published by the Free Software Foundation; either
version 2.1 of the License, or (at your option) any later version.

This library is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
Lesser General Public License for more details.

You should have received a copy of the GNU Lesser General Public
License along with this library; if not, write to the Free Software
Foundation, Inc., 51 Franklin St, Fifth Floor, Boston, MA  02110-1301  USA

Visit our Web Page: www.rdfhdt.org

Contacting the authors:
 - Mario Arias:               mario.arias@deri.org
 - Javier D. Fernandez:       jfergar@infor.uva.es
 - Miguel A. Martinez-Prieto: migumar2@infor.uva.es
 
