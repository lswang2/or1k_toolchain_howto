# or1k_toolchain_howto

# Make directory

mkdir or1k_build
cd or1k_build

# Get sources
git clone git://github.com/lswang2/binutils-gdb
git clone git://github.com/lswang2/or1k-gcc
git clone git://github.com/lswang2/newlib


# Build the first set of tools, binutils etc.

- NOTE: on 32-bit machines --disable-werror is needed due to an enum acting as bit mask is considered signed

mkdir build-binutils build-gcc build-newlib

cd build-binutils

../binutils-gdb/configure --target=or1k-elf --prefix=/usr/local/or1k --enable-shared --disable-itcl --disable-tk --disable-tcl --disable-winsup --disable-libgui --disable-rda --disable-sid --disable-sim --disable-gdb --with-sysroot --disable-newlib --disable-libgloss --disable-werror

make

make install

# Build gcc

cd ../build-gcc

../or1k-gcc/configure --target=or1k-elf --prefix=/usr/local/or1k --enable-languages=c --disable-shared --disable-libssp

make

make install

# build newlib and gdb (without or1ksim in this case)

cd ../build-newlib

../newlib/configure --target=or1k-elf --prefix=/usr/local/or1k --enable-shared --disable-itcl --disable-tk --disable-tcl --disable-winsup --disable-libgui --disable-rda --disable-sid --enable-sim --disable-or1ksim --enable-gdb --with-sysroot --enable-newlib --enable-libgloss --disable-werror

make

make install

# build gcc again, this time with newlib

cd ../build-gcc

../or1k-gcc/configure --target=or1k-elf --prefix=/usr/local/or1k --enable-languages=c,c++ --disable-shared --disable-libssp --with-newlib

make

make install

# Finally, we will want to run the following to put this path in our .bashrc file:

echo "# OpenRISC tool chain path" >> ~/.bashrc

echo "export PATH=$PATH:/usr/local/or1k" >> ~/.bashrc

