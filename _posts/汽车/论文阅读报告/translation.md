
##摘要
柴油发动机的主要排放物有$$$NO_x$$$和$$$soot$$$。本论文介绍中一种旨在同时降低$$$NO_x$$$和$$$soot$$$排放的多次喷射方法，并且提出变喷射压力的新概念，研究它对于发动机排放的影响。

## 介绍
发动机制造商目前面临着提高发动机效率，降低排放题。为了能够在国际汽车市场中具有竞争力，制造商不得不采用更新喷油策略来控制排放和燃油消耗。直喷柴油发动机提供了较好的燃油消耗率，其广泛适用于重型交通工具之中。但是，柴油机在$$$NO_x$$$排放以及$$$soot$$$排放中存在很大的问题[1]。而且，减少这两种排放物的的技术路径常常是相反的，例如：减少喷射时间可以增大喷射压力可降低$$$soot$$$,但是这却会增加$$$NO_x$$$的排放[2]。所以找到一种喷油策略来同步地减少这两种污染物的排放显得尤为重要。现在，包括电子控制技术在内的一些新技术的应用，使得实现这一目标成为可能。多次喷射也被证明可以有效地控制$$$soot$$$和$$$NO_x$$$排放[2-8]。<br>

多次喷射是一个很广泛的概念，它是预喷射，分开喷射等其它一些有多个喷油脉束的喷射方法的总称。预喷射是指在注喷射之前先向燃烧室内喷射少量的燃油，分开喷射是指两次喷油脉束呈一定的角度向燃烧室内喷射，且第一次的喷射量叫后一次多。其它的喷射方法还包括三次喷射，四次喷射等等。本文中，多点喷射就是指分开喷射。<br>

近些年，很多研究者投身于多次喷射策略的研究之中，试图寻找到解决$$$NO_x$$$和$$$soot$$$排放的好方法。Tow等人[4]研究了在重型柴油机中单次，两次，三次喷射对$$$NO_x$$$以及微粒的影响。他们发现两次和三次喷射中缩短喷射时间可以在不提高微粒排放的情况下有效地控制$$$NO_x$$$排放。<br>

Mendes和Thirouard[5]主要研究在低压缩比发动机中用以降低微粒排放，减小噪声和燃油消耗的多点喷射策略。他们的研究结果表明两次喷射可以导致使空气，燃油更好地混合，减少了$$$soot$$$的排放。他们的研究结果还表明降低最高放热率可以有效地减少燃烧噪声。<br>

Husberg等人[6]用实验和CFD模拟的方法研究了在使用预喷射的喷油策略情况下燃烧室内的燃烧现象以及尾气排放。他们的研究结果表明$$$NO_x$$$和$$$soot$$$可以在该喷油策略下得到有效地降低。预喷射的存在使得燃油得到更好的混合。较高的EGR率也会有效地降低燃烧室内的温度，使得预喷射的燃油可以得到较好地混合[7]。<br>

喷射压力在促使燃油和空气得到更好的混合过程中扮演中重要的作用。提高喷射压力可以降低$$$soot$$$排放但是会增高$$$NO_x$$$排放[8]。<br>

大部分的研究者认同预喷射在降低柴油发动机排放物中的积极作用。本文之后会介绍一种更好的分开喷射的喷射模式，并且会研究在预喷射模式下，喷射压力对$$$soot$$$和$$$NO_x$$$排放的影响。

## 发动机建模

KIVA-3V[9]是一款广泛用于发动机模拟的软件。

柴油机燃烧过程模拟可以分为两部分：着火和燃烧。着火过程使用有Halstead等人开发[10]，由Kong等人[11]嵌入到KIVA中的Shell模型。在自动着火阶段燃油达到一定的温度，当达到一定温度时，燃烧模型启动。这一特定温度为1050K。燃烧模型基于Abraham等人[12]研发的层流和湍流模型。

燃油无话模型使用的是由Reitz[13]开发的wave breakup模型。燃油喷射量由喷孔直径和燃油流速决定。燃油的雾化速度由在稳定状态下的分析结果计算得到。油滴的雾化是逐渐由父油滴向子油滴分裂的。其半径变化遵循以下公式：
$$\frac{da}{at} =-\frac {(a-r)}{\tau }$$
其中$$$a$$$代表父液滴的半径，$$$r$$$代表子液滴的半径，分离时间参数$$$\tau$$$定义如下：
$$\tau=\frac{3.726B_1 a}{\Lambda \Omega }                 (2)$$
$$r=B_0\Lambda  (3) $$


泽尔多维奇机理被用于模拟$$$NO_x$$$的形成。Brown[14]解释泽尔多维奇机理可以用下列化学式来表示：
$$O+N_2\leftarrow \rightarrow NO+N(4)$$
$$N+O_2\leftarrow \rightarrow NO+H(5)$$
$$N+OH\leftarrow \rightarrow NO+H(6)$$
局部混合可能会发生反应(7)生成活性氢原子基
$$O+OHx \leftarrow \rightarrow O_2+H(7)$$

$$\frac{d}{dt}[NO]=2K_{1f}[O][N_x]$$
$$\{\frac{1-[NO]^2/K_{1f}[O_2][N_2]} {1+K_{1b}[NO]/(K_{2f}[O_2]+K_{3f}[OH])}\} (8)$$
其中$$$K12=(K_{1f}/K_{1b})(K_{2f}/K_{2b})$$$，下表1,2,3分别对应反应(4)，(5)，(6)。$$$O$$$，$$$OH$$$,$$$O_2$$$和$$$N_2$$$都被假设处于当地热力学平衡状态。Bowman[14]推荐的系数如下：
$$K_{1f}=7.6\times 10^{13}exp(-3800/T)$$
$$K_{1b}=1.6\times10^{13}$$
$$K_{2f}=6.4\times 10^9exp(-3150/T)$$
$$K_{2b}=1.5\times 10^9exp(-19500/T)$$
$$K_{3f}=1.0\times10^{14}$$
$$K_{3b}=2.0\times 10^14exp(-23650/T)$$
Hiroyasu和Nagle-Strickland-constable模型被用于$$$soot$$$生成和氧化[15,16]。Hiroyasu模型通过预测$$$soot$$$初始生成量$$$M_{sf}$$$和$$$soot$$$氧化量$$$M_{so}$$$来预测$$$soot$$$最终生成量$$$M_s$$$，公式如下：
$$\frac{d(M_s)}{dt}=M_{sf}-M_{so}(12)$$

其中$$$M_{sf}$$$和燃料蒸汽团$$$M_{fv}$$$有关：
$$M_{sf}=K_fM_{fv}$$
其中常数$$$K_f$$$满足下列公式：
$$K_f=A_{sf}P^{0.5}exp(-E_sf/RT)$$
Nagle-Strickland-constable模型中$$$M_{so}$$$和$$$M_s$$$成比例：
$$M_{so}=K_0M_s$$
其中$$$K_0$$$与分子质量$$$M_{w_c}$$$，$$$M_s$$$，微粒直径$$$D_s$$$，微粒密度$$$\rho_s$$$和气体常数$$$R_{axid}$$$有关：
$$K_0=\frac{6}{\rho_s D_s}M_{w_c}\cdot M_s\cdot R_{axid}$$
湍流模型选用$$$K-\varepsilon$$$模型[9]。

## 燃烧模型的标定
燃烧模型的标定基于在柴油发动机MT4.244的实验标定数据，发动机参数和工作状态列在表1中：

|  表一  |发动机参数|
|--------|--------|
| 气缸直径$$$\times$$$冲程(mm)|  100$$$\times$$$127  |
|连杆长度(mm)|219|
| 压缩比 |  17.5 |
| 喷嘴个数  | 5  |
| 喷射锥角($$$^\circ$$$)  |  14.5 |
| 喷雾夹角($$$^\circ$$$) |  55 |
| 燃烧室  |   |
| 活塞形状  | Omega  |
| 进气压力(KPa)  | 233  |
|进气温度(K)|420|
| 进气门关闭时间($$$^\circ$$$,TDC) |  -150 |
|螺旋半径|1.8|
|发动机转速(r/min)|2000|
|喷油始点($$$^\circ$$$)|+2|
|喷油压力(Bar)|250|

测试仪器使用表2 中所示仪器：

|||
|--|--|
|压力传感器|GU22C|
|$$$NO_x$$$分析仪|AVL Dicom4000气体分析仪|
|烟度计|AVL 415烟度计|

![fig1](F:\ivyxjcUniversity\translation\images\fig1.png)
图1：(a)底视图(b)俯视图(c)主视图(d)3D图<br>


燃烧室由ANSYS ICEM CFD10进行网格化，如图1所示。其中共有80000个网格。

为了在实验数据的基础上更准确地计算模拟结果，缸内压力变化曲线，废弃中$$$soot$$$和$$$NO_x$$$含量都将被用于其中。表3为两种排放物的预测值和测量值。图2表明实验得到的缸内压力变化曲线和计算得到的压力变化曲线基本一致。

|排放物($$$gr/kW\cdot h)$$$|测量值|预测值|
|---|---|---|
|$$$soot$$$|0.95|1.02|
|$$$NO_x$$$|6.84|7.68|

![fig2](F:\ivyxjcUniversity\translation\images\fig2.png)

本次研究的重点是喷油次数，喷油持续期，喷油压力和每次喷油量和喷油间隔对最终排放物的影响。以此取得可以使得$$$NO_x$$$和$$$soot$$$排放都较低的一个平衡点。

为了使喷油模式的描述更为简单，我们用下面这个格式来描述喷油模式：第一次喷油量(喷油间隔)第二次喷油量-第一次喷油时间。例如，90(8)10-2表示第一次喷90%的油，隔$$$5^\circ CA$$$喷第二次油，第二次喷油量为10%，第一次喷油始点在上止点后$$$2^\circ CA$$$。随着前后喷油量不同，这些喷油模式可分为预主喷模式和主后喷模式。

## 结果讨论
本论文共研究了6种喷油模式，分别为单次喷射，10(5)90-2，25(5)75-2，50(5)50-2，75(5)25-2，90(5)10-2。放热率和缸内压力图如图3所示
![fig3_1](F:\ivyxjcUniversity\translation\images\fig3_1.png)
![fig3_2](F:\ivyxjcUniversity\translation\images\fig3_2.png)
![fig3_3](F:\ivyxjcUniversity\translation\images\fig3_3.png)
由图中我们可以清楚地看到第二次喷射的喷油量为90%时，其最高放热率最低，这是因为在此情况下，燃油的混合并不好。此外，此时缸内压力曲线下的面积也变小了，这说明发动机动力收到了削弱。本次研究的目的要求是在不影响发动机动力的情况下减少排放。所以最好的模式肯定是在第一次喷油时即喷射大部分燃油。<br>

表4:

|喷射模式|$$$soot(gr/kW\cdot h)$$$|$$$NO_x(gr/kW\cdot h)$$$|
|-----|---|---|
|单次喷射|1.02|7.68|
|10(5)90-2|3.51|3.58|
|25(5)75-2|2.76|6.50|
|50(5)50-2|2.59|6.8|
|75(5)25-2|1.26|7.32|
|90(5)10-2|1.12|7.56|
表4展示了在这6中模式下$$$soot$$$和$$$NO_x$$$的排放量。随着第二次喷射的喷油量的增加，$$$NO_x$$$含量逐渐降低，$$$soot$$$排放量逐渐增多。这是因为$$$NO_x$$$的形成条件为高温富氧，第二次喷油量增加，放热率降低，温度降低，导致$$$NO_x$$$降低。而且此时因为混合并不均匀，燃烧不够充分，$$$soot$$$排放增加。

所以找到一个平衡点，在该点出，放热率维持上述水平以维持较低的$$NO_x$$排放量，且可以进一步促成$$$soot$$$氧化，降低$$$soot$$$含量。我们采用在75(5)25-2和90(5)10-2基础上增大两次喷射的喷油间隔来进一步寻找更好的喷油模式。

图4展示了75($$$\alpha$$$)25-2喷油模式下的放热率曲线和缸内压力曲线，其中$$$\alpha$$$取值8,20,30,35和40$$$^\circ CA$$$。
![fig4_1](F:\ivyxjcUniversity\translation\images\fig4_1.png)
![fig4_2](F:\ivyxjcUniversity\translation\images\fig4_2.png)

图4表明增大喷油间隔并不会改变气缸最高压力。此外，随着喷油间隔的逐渐增大，逐渐形成了一个由第二次喷油引起的放热率的次高峰。这一现象展示了整个燃烧过程的最后一步，由第二次喷射引起的一次快速的预混，扩散燃烧。由90($$$\alpha$$$)10-2喷油模式得到的数据和75($$$\alpha$$$)25-2的基本相同，本论文并未予以展示。





## 参考文献
[1]  D. A. Pierpont and R.  D. Reitz, Effects of injection pressureand nozzle geometry on emissions and  performance in a D.Idiesel, SAE Paper 950604, 1995.
[2]  T. F. Su, M. A.  Patterson, R. D. Reitz and P. V. Farrell,  Ex-perimental and  numerical studies  of high  pressure multipleinjection sprays, SAE Technical Paper 960861, 1996.
[3]  T. C. Tow, D. A Pierpont and R. D. Reitz, Reducing particu-late and NOx emissions by  using  multiple  injections  in axheavy duty DI diesel engine, SAE Paper 950897, 1995.
[4]  S.   Mendez  and   B.  Thirouard,   Using  multiple   injectionstrategies in  diesel combustion:  potential  to improve  emis-sions, noise and  fuel economy trade-off in  low CR engines,SAE Technical Paper 2008-8-01- 1329, 2008.
[5]  M. Halstead, L. Kirsch and  C. Quinine, The auto ignition ofhydrocarbon fueled  at high temperature and  pressure fittingof mathematical  model, Combustion Flame,  30 (45) (1997)45-60.
[6]  Y.  Liu, F.  Tao, D.  Foster and  R. D.  Reitz,  Application of multiple-step phenomenological soot  model to HSDI dieselmultiple injection modeling, SAE  Technical Paper 2005 01-0924, 2005.
[7]  T. Lee, An experimental study  of emission reduction mecha-nisms in a high speed direct injection diesel engine with mul-tiple injection and EGR, PhDs Thesis, University of Wiscon-sin-Madison, USA (2002).
[8]  J.  B. Heywood,  Internal  combustion engine  fundamentals,McGraw-Hill Publishing Company, New York, USA (1998).
[9]  A. A. Amsden, P. J. O’ Rourke and T. D. Butler, KIVA-II: Acomputer program for chemically reactive flows with sprays,Los   Alamos  National   Laboratory,   LA-11560-MS,  USA(1989).
[10]  M. P. Halstead,  L. J. Kirsch, A.  Prothero and C. P. Quinn,A mathematical model for hydrocarbon auto ignition at highpressures, Proc. R. Soc. Lond. A., 364 (1975) 515-538.
[11]  S. -C. Kong, Z. Han and R. D. Reitz, The development andapplication  of a  diesel  ignition and  combustion  model formultidimensional  engine  simulation,   SAE  Paper  950278,1995.
[12]  J. Abraham, F. V. Bracco  and R. D. Reitz, Comparisons ofcomputed  and measured  premixed  charge engine  combus-tion, Combustion and Flame, 60 (1985) 309-322.
[13]  R.  D.   Reitz,  Modeling   atomization  processes  in   high-pressure  vaporization spray,  Atomization  and  Spray  Technology, 3 (1987) 309-37.
[14]  C. T. Bowman, Kinetics of pollutant formation and destruction  in combustion,  Prog. Energy  Combust.  Sci., 1  (1975)33-45.
[15]  M.  A. Patterson,  S.-C.  Kong,  G. J.  Hampson  and  R. D.Reitz, Modeling  the effects  of fuel  injection characteristicson diesel engine soot and NOx emission, SAE Paper  940523,1994.
[16]  J. Nagle  and R. F. Strickland-Constable,  Oxidation of car-bon  between 1000-2000º  C, Int.  Journal  of Carbon,  1 (3)(1964) 333-338.
[17]  D. A. Nehmer  and R. D.  Reitz, Measurement of the  effectof injection rate and split injections on diesel engine soot andNOx emissions, SAE Paper 940668 (1994).
[18]  S.  Shundoh, M.  Komori, K.  Tsujimur  and S.  Kobayashi,NOx reduction from  diesel combustion using pilot  injectionwith high pressure fuel injection, SAE Paper 920461 (1992).
[19]  D. T. Montgomery and R. D. Reitz, Six-mode cycle evalua-tion of the effect of  EGR and multiple injections on particulate and NOx emissions from a D.I. diesel Engine, SAE Paper 960316(1996).
[20]  D. A. Nehmer  and R. D.  Reitz, Measurement of the  effectcombustion simulation and experiment in internal combustion engines, diesel engines performance, and emission reduction. 
[21]  K.  Poorghasemi,  F. Ommi  and  V.  Esfahanian, Effect  ofhigh pressure post injection on soot and NO trade off in a DIdiesel engine, ASME Technical Paper, IMECE2010-307013,
British Columbia Uni., Canada (2010).
[22]  M. K. Bobba,  M. P. B. Musculus, Effect  of post injectionson cylinder  and exhaust  soot for  low temperature  combus-tion  in  a heavy-duty  diesel  engine,  SAE  Technical  Paper
2010-01-0612, 2010.



