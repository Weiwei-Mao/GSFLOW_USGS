# GSFLOW

引用格式
>Markstrom, S.L., Niswonger, R.G., Regan, R.S., Prudic, D.E., and Barlow, P.M., 2008, GSFLOW—Coupled ground-water and surface-water flow model based on the integration of the Precipitation-Runoff Modeling System (PRMS) and the Modular Ground-Water Flow Model (MODFLOW-2005): U.S. Geological Survey Techniques and Methods 6-D1, 240 p.

## Abstract
GSFLOW (Ground-water and Surface-water FLOW)，基于USGS的Precipitation-Runoff Modeling System (PRMS)和MODFLOW耦合而成。此外，为了更容易耦合，增加且修改了原始模型中的某些组件。该模型发展了求解PRMS水文响应单元到MODFLOW有限差分网格之间水流流动的计算方法。本报告描述了GSFLOW所有组件的组织、概念、设计和数学公式。耦合模型非常重要的一部分就是保证区域水量均衡的能力，和提供所研究就区域的综合水分收支情况。这篇报告也包含了耦合模型和单个模型水量收支情况的计算。

## Introduction
### Integrated Hydrologic Models
设计耦合模型时，一般存在两种方法。一种是“fully integrated”方法，该方法时将地表水与地下水流方程同时求解。另一种方法是将地表与地下系统划分至不同的区域，在不同的区域采用不同的控制方程描述，再通过迭代耦合的方法将二者耦合在一起。第二种方法称为“coupled regions”。   

全耦和方法需要求解三维Richards方程，对于模拟尺度成百上千公里，模拟时间从月到几十年的区域水文系统，是不可行的。

在很大区域垂向平均的情况下，非饱和带水分主要是在垂向运动，该特点导致了一个对于耦合模型中模拟非饱和带运动是非常有效的方法。因此，可以分别模拟土壤、非饱和、饱和水分运动，牺牲一部分精度换取模型计算效率（GSFLOW将非饱和带上部分作为soil water，下部分作为unsaturated zone，然后是Groundwater flow）。

GSFLOW是用来同时模拟一个或数个流域中的地表、地下饱和带和非饱和带的水分流动的。

选择PRMS的原因（1）可以模拟蒸散发、地表径流、入渗和

## Design of GSFLOW
GSLOW模拟的流动在三个区域中。第一个区域是从作物冠层到土壤层；第二个区域是包含所有的水流和湖泊；第三个区域是土壤层以下的区域。PRMS模拟第一个区域，MODFLOW-2005模拟第二个和第三个区域。模型设计基于以下原则：
1、如果可能的话，尽量采用已有的PRMS和MODFLOW程序包；
2、采用灵活且自适应的模块化编程方法，以包含所有PRMS和MODFLOW-2005的程序框架，这样以后这两个程序的新技术也可以被加进GSFLOW；
3、采用总体设计程序，以方便其他模型加入GSFLOW；
4、允许单独运行PRMS和MODFLOW-2005，目的是初始的模型校验。因为耦合模型一起率定参数过于复杂；
5、迭代求解地表、地下控制方程；
6、计算模型所有空间时间所有分区详细的水均衡结果；
7、允许灵活的PRMS地表水文相应单元的划分和MODFLOW有限单元的划分；
8、允许模型边界采用定水头边界、定流量边界、依赖于水头的边界定义，以此来代表区域的入流和出流。






