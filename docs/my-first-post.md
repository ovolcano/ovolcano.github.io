---

title: ovolcano的学习笔记

date: 2026-07-31

---

## GROMACS命令

由pdb生成gro：

gmx editconf -f input.pdb -o output.gro -box 5 5 5

进行扩胞：

gmx genconf -f output.gro -nbox 2 2 3 -o output\_large.gro



top文件中\[ molecules ]中各个组分的顺序必须和gro文件一致

