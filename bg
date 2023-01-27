> pdat<-read.csv('ordered_coldat3.csv')
> sampleNames(bg)%in%pdat$X
  [1] TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE
 [16] TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE
 [31] TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE
 [46] TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE
 [61] TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE
 [76] TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE
 [91] TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE
> pdat2<-pdat[match(sampleNames(bg),pdat$X)),]
> phenodat<-data.frame(id=as.vector(pdat2$X),country=as.vector(pdat2$country),tissue=as.vector(pdat2$tissue),cultivar=as.vector(pdat2$cultivar),subspecies=as.vector(pdat2$subspecies),variety=as.vector(pdat2$variety),path=as.vector(fidir))
> pData(bg)=phenodat



> library(genefilter)
> bgfiltered<-subset(bg,'rowVars(texpr(bg))>1',genomesubset=T)
> bgfiltered
ballgown instance with 42241 transcripts and 100 samples
> bgdomwild<-subset(bgfiltered,"variety=='europaea' | variety=='sylvestris'",genomesubset=F)
> debgdomwild<-stattest(bgfiltered,feature='transcript',covariate='variety',getFC=TRUE,meas='FPKM')
Error in stattest(bgfiltered, feature = "transcript", covariate = "variety",  : 
  There must be at least two replicates per group. Make sure covariate is categorical; if continuous, consider the timecourse option, or specify your own models with mod and mod0.
> debgdomwild<-stattest(bgdomwild,feature='transcript',covariate='variety',getFC=TRUE,meas='FPKM')
> head(debgdomwild)
     feature id        fc         pval         qval
1 transcript  1 1.1353687 5.345199e-02 1.070079e-01
2 transcript  2 1.0020758 9.830746e-01 9.888804e-01
3 transcript  3 1.8690875 3.452051e-04 1.582915e-03
4 transcript  6 0.5068717 1.218422e-09 7.363001e-08
5 transcript  7 2.3275775 1.297218e-03 4.850473e-03
6 transcript 11 2.7821678 1.244879e-05 9.752396e-05
> write.csv(debgdomwild,'debgdomwild.csv')



> gexflt=as.data.frame(gexpr(bgfiltered))
> write.csv(gexflt,'gexflt.csv')
> transcriptgenetab=indexes(bgfiltered)$t2g
> head(transcriptgenetab)
   t_id     g_id
1     1 MSTRG.22
2     2  MSTRG.1
3     3  MSTRG.2
6     6  MSTRG.5
7     7  MSTRG.6
11   11 MSTRG.10
> length(row.names(transcriptgenetab))
[1] 42241
> length(unique(transcriptgenetab[,'g_id']))
[1] 38090
