# If the or1k tools chains are not compiled at centos or RHEL, we have to compile new latest gcc,binutils on linux.

> //required libraries:<br>
> yum install libmpc-devel mpfr-devel gmp-devel zlib-devel<br>
> ../gcc/configure --prefix=/usr/local --with-system-zlib --disable-multilib --enable-languages=c,c++<br>
> make -j 8<br>
> make install<br>

> //install new binutils
> wget 'http://ftp.gnu.org/gnu/binutils/binutils-2.30.tar.xz'<br>
> tar xvf binutils-2.30.tar.xz<br>
> mkdir build<br>
> ../configure --prefix=/usr/local --enable-shared --disable-itcl --disable-tk --disable-tcl --disable-winsup --disable-libgui --disable-rda --disable-sid --disable-sim --enable-gdb --with-sysroot --disable-newlib --disable-libgloss --disable-werror<br>
> make<br>
> make install


