\# LAMMPS安装教程

\## 首先安装必要的依赖

conda create -n lammps

conda activate lammps

conda install cmake

conda install -c conda-forge gcc\_linux-64

conda install -c conda-forge gxx\_linux-64

conda install -c conda-forge gfortran\_linux-64

conda install -c conda-forge openmpi

conda install libfftw3-dev

conda install build-essential

\## 解压安装包

tar -xzvf lammps-stable.tar.gz

\## 为编译做准备

cd lammps-22Jul2025/

mkdir build/

cd build/

cmake ../cmake -D BUILD\_MPI=on -D PKG\_MANYBODY=on -D PKG\_KSPACE=on -D PKG\_MOLECULE=on -D PKG\_COLVARS=on -D PKG\_EXTRA-DUMP=on -D PKG\_RIGID=on -D PKG\_GPU=on -D PKG\_KOKKOS=on -D PKG\_CLASS2=on

\## 有些包需要在lib里先编译一遍         

cd ../lib/colvars/

python3 Install.py -m mpi

cd ../lepton/

python3 Install.py -m mpi

cd ../electrode/

python3 Install.py -m mpi

\## 最后进行编译和安装

cd ../../build/

make -j 32

make install

cd ../src

make mpi -j 32

\## 运行模拟

lammps-22Jul2025/build/lmp -in lammps.in -log out.log

