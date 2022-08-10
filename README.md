
# MingPCACluster
A new simple and efficient software to PCA and Cluster For popolation VCF File or STOmics gem File 

###  1 Introduction
<b>MingPCACluster</b>  ���ڻ���VCF������PCA�����;��������ͬʱ�沢��Genotype �ȸ�ʽ�����ͬʱ�������ʱ�յ�ϸ��������ĸ�ʽ��xx.gem.gz���ļ���beta���ܣ���
��ֻҪ��Ӧ��һ�������ļ���������PCA����ͼ�����һλ��λ��
</br>
</br> keyword  : VCF2PCA ;&nbsp;&nbsp;&nbsp;&nbsp;    VCF2Kinship ;&nbsp;&nbsp;&nbsp;&nbsp; cluster;&nbsp;&nbsp;&nbsp;&nbsp; k-means ;&nbsp;&nbsp;&nbsp;&nbsp; cellbin ;&nbsp;&nbsp;&nbsp;&nbsp;STOmics

</br>���㣺
</br>1  The result is the same with [tassel](https://www.maizegenetics.net/tassel),[gapit](https://zzlab.net/GAPIT/) and [gcta](https://yanglab.westlake.edu.cn/software/gcta/#Overview) , just the difference in precision.
</br>2  ������ 1 ����kinship���� 2  PCA��� 3  ������  ��4 ��clusterȾɫ����ͼ��
</br>3  һ��VCF���룬һ����λ�������û�ʹ��.
</br>4  �߶����㣬�ڴ������λ����ٵ�Ӱ�죨ʱ�����ǰ����ܻ����������ٵ�Ӱ�죩���ڴ�ֻ����Ʒ��Ӱ�죬����100k����Ʒ��Ҳ�У�����������Ͽ���ʱ��ϸ��PCA�;���,��Ȼʱ����ѧ����Ҫ����Ʒ�ࡣ��80K 60G�ڴ棩
</br>5  Kmean������������ҳ����Kֵ����Structure��Kֵһ��. ��ͼ�Դ�Ⱦɫ��
</br>6  ������ͼС�ű�������������ű��Ż���ͼ�ȡ�

</br>

</br>�����Ǹ�һЩ�л��������������õģ�����С�׿����������ˡ�
</br>
</br><b>MingPCACluster</b> MingPCAC is a PCA analysis software format developed based on VCF. It also incorporates Genotype, etc., and develops a file (beta function) for the expression of spatiotemporal cells. That is, as long as the input is satisfied, the PCA and the cluster group are of the same output.


###  2 Download and Install
------------
The <b>new version</b> will be updated and maintained in <b>[hewm2008/MingPCACluster](https://github.com/hewm2008/MingPCACluster)</b>, please click below website to download the latest version
</br><p align="center"><b>[hewm2008/MingPCACluster](https://github.com/hewm2008/MingPCACluster)</b></p>

<b> 2.1. linux/MaxOS&nbsp;&nbsp;&nbsp;   [Download](https://github.com/hewm2008/MingPCACluster/archive/v1.09.tar.gz)</b>
  
  </br> <b>2.2 Pre-install</b>
  </br> MingPCACluster is for Linux/Unix/macOS only.
  </br>Before installing,please make sure the following pre-requirements are ready to use.
  </br> 1) [convert](https://linux.die.net/man/1/convert) command is recommended to be pre-installed, although it is not required
  </br> 2) g++   : g++ with [--std=c++11](https://gcc.gnu.org/) > 4.8+ is recommended
 ?</br> 3) zlib  : [zlib](https://zlib.net/) > 1.2.3 is recommended
 ?</br> 4) R     : [R](https://www.r-project.org/) with [ggplot](http://ggplot.yhathq.com/) is recommended

</br> <b>2.3 Install</b>
</br> Users can install it with the following options:
</br> Option 1: 
<pre>
        git clone https://github.com/hewm2008/MingPCACluster.git
        cd MingPCACluster;	chmod 755 -R bin/*
        ./bin/MingPCACluster  -h 
</pre>


###  3 Parameter description
------------
</br><b>3.1 MingPCACluster</b>
</br><b>3.1.1 Main parameter</b>

```php

	Usage: MingPCACluster  -InVCF  <in.vcf.gz>  -OutPut <outPrefix>

		-InVCF        <str>      Input SNP VCF Format
		-InGenotype   <str>      InPut Genotype File
		-InKinship    <str>      Input SNP K Kinship File Format
		-OutPut       <str>      OutPut File Prefix(Kinship PCA etc)

		-Method       <int>      Method of Kinship [1-4],defaut [1]
		                         1:BaldingNicolsKinship(VanRaden/Normalized_IBS)
		                         2:IBSKinshipImpute 3:IBSKinship 4:p_dis

		-help                    Show more Parameters and help [hewm2008]


```
</br> brief description for function:
<pre>
	   #   �÷�һ���������������Ϊ һ�������������� 
     #       �����ļ��������ʽ��  pdf.��ҪΪVCF��gem�ļ�
	   #    ����˵�����潫��֪������

	    MingPCACluster	-InSTOgem	Test.gem.gz	-OutPut	Test	-CellBin	100

          ### run without pop.info
          #   MingPCACluster	-InVCF	Khuman.vcf.gz	-OutPut	OUT
          ### run with  pop.info
        MingPCACluster	-InVCF	Khuman.vcf.gz	-OutPut	OUT	-InSampleGroup	pop.info 

</pre>

</br><b>3.1.2  Detail parameters</b>
```php

	Usage: MingPCACluster  -InVCF  <in.vcf.gz>  -OutPut <outPrefix>

		-InVCF        <str>      Input SNP VCF Format
		-InGenotype   <str>      InPut Genotype File
		-InKinship    <str>      Input SNP K Kinship File Format
		-OutPut       <str>      OutPut File Prefix(Kinship PCA etc)

		-Method       <int>      Method of Kinship [1-4],defaut [1]
		                         1:BaldingNicolsKinship(VanRaden/Normalized_IBS)
		                         2:IBSKinshipImpute 3:IBSKinship 4:p_dis

		-help                    Show more Parameters and help [hewm2008]

		-InSampleGroup <string>   In File of sampleGroup info,format(sample groupA)

		-MAF           <float>    Min minor allele frequency filter [0.001]
		-Fchr          <str>      Filter the chrX chr[chrX,chrY,X,Y]
		-Miss          <float>    Max ratio of miss allele filter [0.25]
		-Het           <float>    Max ratio of het allele filter [1.00]
		-HWE           <float>    Exact test of Hardy-Weinberg Equilibrium for SNP Pvalue[0]
		-SubPop        <str>      Sub Sample File List to PCA[ALLsample]
		-KeepRemainVCF            keep the VCF after filter
		
		-InSTOgem      <str>      InPut STOmics gem File of MIDCounts(beta)
		-CellBin       <int>      STOmics cell bin[50]
		-STOName       <string>   STOmics Sample Name STOName


		-PCANum        <int>      Num of PCA eig [10]
		-MaxCluNum     <int>      Max Cluster Num to find Best K [12]
		-BestKRatio    <float>    Get the best K Cluster by deta-SSE Ratio[0.15]


```

</br><b>3.2.2 Other parameters</b>
</br>����Ҳ�ṩ����ͼ���perl ��ͼ�ű�������ű����潫���Ż������ϴ���Ҫ�����ʱ���æ������ͼ�ű��ļ�Ҫ����˵�����£�

```php
ploteig  -h

	Version:1.04         hewm2008@gmail.com

	Usage: ploteig  -InPCA  pca.eigenvec -OutPrefix Fig


		Options

		-InPCA        <s>   : InPut File of PCA
		-OutPrefix    <s>   : OutPut file prefix

		-help               : Show more help [hewm2008]

		-columns      <s>   : the columns to plot a:b [3:4]
		-ColShap            : colour <=> shape for cluster or subpop
		-border       <i>   : how to plot the border (1,2,4,8,3,31) [3]
		-title        <s>   : title (legend) [PCA]
		-keystyle     <s>   : put key at top right  default(in) [outside]box [outside]
		-pointsize    <i>   : point size for plot [3]

		-BinDir       <s>   : The Bin Dir of gnuplot/R/ps2pdf/convert [$PATH]

```

</br><b>3.3 Output files</b>


|Module |    outFlie    |       Description                                                |
|:-----:|:-------------------|:------------------------------------------------------------|
| List  |                    |                                                             |
|       |out.kinship         |�������Ե���󣬸���Ʒ��������ϵ                             |
|       |out.eigenvec        |������ž����pca���                                        |
|       |out.eigenval        |���pca�������������                                        |
|       |out.PCA1_PCA2.pdf   |�����clusterȾɫ���pca 1 2ͼ                               |
|       |out.K.pdf           |���cluster Kͼ  ��SSE BDi��                                 |
|       |out.cluster         |����ĸ���K��cluster������                                 |
|       |Out.cellbin.gz      |���bin50 cell�Ľ�������� -InSTOgem                         |
|       |Out.cluster pdf/png |�������cluesterͼ������-InSTOgem                            |


ʾ��ͼ������Ӧ�ó�������ͼ��ʾ��ͼ�͸�ʽ��һ�����������ͼ���Լ�example 1 ��2


###  4 Example
------------

</br>See more detailed usage in the&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <b>[Chinese Documentation](https://github.com/hewm2008/MingPCACluster/blob/main/MingPCAClusterʹ���ֲ�_manual_chinese.pdf)</b>
</br>See more detailed usage in the&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <b>[English Documentation](https://github.com/hewm2008/MingPCACluster/blob/main/MingPCAClusterʹ���ֲ�_manual_chinese.pdf)</b>
</br>See the example directory and  Manual.pdf for more detail.
</br>��������  Manual.pdf for more detail �����ʾ�����ݺͽű������ڽ���ĳЩ��ַ�ͷ�һЩ�̳�
</br></br> 
../../bin/MingPCACluster      -InVCF        in.vcf.gz     -OutPut outPrefix
</br>  Ŀ¼  Example/example*/�����������������ͽű��÷���


* Example 1)ǧ��VCF�ز���SNP������
</br> ����K ������chr22  dbsnp�������������1194��λ�㣬�� CEU��49�� �� CHB��46�� �� JPT��56���� YRI ��52����203 ����Ʒ��������
</br>�������ƣ�best K
</br>![K_SSE.png](https://github.com/hewm2008/MingPCACluster/blob/main/example/Example1/K_Eva.png)
</br>PCA���
</br>![PCA.png](https://github.com/hewm2008/MingPCACluster/blob/main/example/Example1/PCA.png)


* Example 2) cellbinʱ��ϸ�������pca�;���  

</br>ʱ�շ����ҳ��˽���Ҫ�ǣ�seurat ���Һ�ǳ�����˽⣬������õ���n*m (n����Ʒ��m��λ��)��ϡ����󣬺����ܱߵ���ʱ�յ�����˵�ڴ�ܴ�����û�ж�ʱ���������У��Ա����������ȡlog10. Ҳ����ϡ����� �� n*n, ����ʱ��n����Ʒ���ܴ������½���
</br>���� ���������ļ�����(File.gem.gz : 177M )�� ��Χ�� XXmin:        4975    XXmax:  23374   YYmin:  2525    YYmax:  20724 )��ȡbin 50�� n�ﵽ��88507������Ҫ88507*88507�ľ���double�ϣ�ռ��60.742G (ϡ�����5G   ����:55G) ��

</br> PCA K Fig
</br>![out1.png](https://github.com/hewm2008/MingPCACluster/blob/main/example/Example2/OUT1.png)
</br> PCA plot Fig
</br>![out2.png](https://github.com/hewm2008/MingPCACluster/blob/main/example/Example2/OUT2.png)
</br> STOmics Cluster plot Fig
</br>![out3.png](https://github.com/hewm2008/MingPCACluster/blob/main/example/Example2/OUT3.png)


###  5 Advantages

</br>�ٶȿ죬���ڴ�    fast speed, low memory
</br>��������    Simple and easy to use
</br>�ⰲװ   Free installation


###  6 Discussing
------------
- [:email:](https://github.com/hewm2008/MingPCACluster) hewm2008@gmail.com / hewm2008@qq.com
- join the<b><i> QQ Group : 125293663</b></i>

######################swimming in the sky and flying in the sea #############################

