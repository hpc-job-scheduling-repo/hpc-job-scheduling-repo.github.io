---
layout: default
title: Wall Time Trediction
---

For more than two decades, researchers have been developingmethods to predict HPC job runtimes. The methods vary from simplerule-based solutions to modern methods using machine and deep learninglibraries. 


This is a collection of these methods and their results. This is to ensure a better comparability and sustainability. Feel free to contribute your results.


# Metrics
To better compare the solutions, the same metrics should be used. The metrics proposed here should rather be seen as initial metric sand can be extended or changed after discussion with the community.
Scikit-learn offers ready to use functions which calculates regression metrics based on the predicted and used wall time.
Details can be obtained from the [Sci-Kit docs](https://scikit-learn.org/stable/modules/classes.html#module-sklearn.metrics)
<!-- $$ \text{MAE}(y,\hat{y}) = \frac{1}{n_\text{samples}}\sum_{i=0}^{n_\text{samples}-1}|y_i-\hat{y_i}|$$ -->
* Sci-Kit Regression metrics Mean Absolute Error (MAE) and Median Absolute Error (MedAE)

* Processing time (excluding initial workload parsing)

* Over- and under-estimates

* ...


# Predictioner

### ALEA Predictioner

Alea uses previously known run times, of already completed jobs, to establish a run time estimate for 
a newly arriving job. It is working on a per-user basis, i.e., a new run-time 
estimate for a given job is computed using information about previous jobs of that user.

$$ \sigma(i) := \frac{T_\text{Run}(i)}{T_\text{Req}(i)} $$ 

Once $$\sigma$$ is computed, it is used to predict wall times. 
The predictor only uses the last five (most 
recently completed) jobs, when computing the prediction.  

$$ T_\text{Prediction}(i) := T_\text{Requested}(i) \max_{i-5 \leq k \leq i-1} \{\sigma(k)\} $$

Results of processing various logs from the [Parallel Workload Archive](https://www.cs.huji.ac.il/labs/parallel/workload/logs.html). The original implementation is built into the ALEA Scheduling Simulator which can be found [here](https://github.com/aleasimulator/alea). A reimplementation in Python can be found [here](https://github.com/mehsoy/walltime-prediction-tools). Results below where done by using the reimplementation.


|Source|Language & Tools|Hardware
|:-------------|:------------------|:------|
|[walltime-predictioner-alea.py](https://github.com/mehsoy/walltime-prediction-tools/blob/master/walltime-predictioner-alea.py) | Python 3.8 + Pandas | Intel 6700T | 




|Workload|MAE (s)|MedAE (s)|Processing time
|:-------------|:------------------|:------|
|ANL-Intrepid-2009-1.swf.gz|1928|134|3.60
|CEA-Curie-2011-2.1-cln.swf.gz|11002|186|15.30
|CTC-SP2-1995-2.swf.gz|7915|261|4.50
|CTC-SP2-1996-3.1-cln.swf.gz|7118|636|4.60
|HPC2N-2002-2.2-cln.swf.gz|8984|78|10.40
|KIT-FH2-2016-1.swf.gz|15291|352|6.00
|KTH-SP2-1996-2.1-cln.swf.gz|3879|189|1.60
|LANL-CM5-1994-4.1-cln.swf.gz|5865|646|6.20
|LANL-O2K-1999-2.swf.gz|4173|254|6.20
|LCG-2005-1.swf.gz|4834|116|9.20
|LLNL-Atlas-2006-2.1-cln.swf.gz|23525|87|2.30
|LLNL-T3D-1996-2.swf.gz|1115|29|1.30
|LLNL-Thunder-2007-1.1-cln.swf.gz|54346|25|6.20
|LLNL-uBGL-2006-2.swf.gz|161|0|5.30
|LPC-EGEE-2004-1.2-cln.swf.gz|4912|14|11.80
|METACENTRUM-2009-2.swf.gz|11972|303|5.00
|NASA-iPSC-1993-3.1-cln.swf.gz|694|45|1.00
|OSC-Clust-2000-3.1-cln.swf.gz|18569|250|2.10
|PIK-IPLEX-2009-1.swf.gz|16167|44|35.30
|RICC-2010-2.swf.gz|5504|40|21.10
|SDSC-BLUE-2000-4.2-cln.swf.gz|3434|255|12.40
|SDSC-DS-2004-2.1-cln.swf.gz|6020|172|5.20
|SDSC-Par-1995-3.1-cln.swf.gz|3127|18|2.70
|SDSC-Par-1996-3.1-cln.swf.gz|4652|92|1.60
|SDSC-SP2-1998-4.2-cln.swf.gz|5491|284|3.60
|SHARCNET-2005-2.swf.gz|9403|90|57.60
|SHARCNET-Whale-2006-2.swf.gz|8880|519|31.00
|Sandia-Ross-2001-1.1-cln.swf.gz|60345|4224|4.00
|UniLu-Gaia-2014-2.swf.gz|14373|88|2.70




### More comming soon



