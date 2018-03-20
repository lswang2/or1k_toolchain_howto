# If the or1k tools chains are not compiled at centos or RHEL, we can compile new latest gcc on linux.

> //required libraries:<br>
> yum install libmpc-devel mpfr-devel gmp-devel zlib-devel<br>
> ../gcc/configure --prefix=/usr/local --with-system-zlib --disable-multilib --enable-languages=c,c++<br>
> make -j 8<br>
> make install<br>
