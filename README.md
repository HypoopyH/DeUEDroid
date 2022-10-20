# DeUEDroid: An UEware Detection System Based on UTG
Introduction and implementation of the paper DeUEDroid: An UEware Detection System Based on UTG.
## Introduction
Nowadays, apps that serve the underground economy are prevalent nowadays.
Unlike legitimate apps (e.g., pornhub in the US), these apps serve the underground economy by providing illegal sensitive services (e.g., gambling scam, prostitution, Ponzi scheme, usury).  We call them underground economy apps, or *UEware* for short. However, traditional malicious detection
methods cannot effectively address this emerging threat.

To address this problem, we propose a novel approach to effectively and efficiently detect UEware by considering their UI transition graphs (UTG). Based on the proposed approach, we design and implement a system, named DeUEDroid, to perform the detection. To evaluate DeUEDroid, we collect 26, 591 apps to evaluate DeUEDroid and build up the first large-scale ground-truth UEware dataset (1, 720 underground economy apps and 831 legitimate apps)

## Motivation Example
To perform an effective large-scale detection, we propose a UEware detection approach based on the UTG. Our approach is based on two key observations:
1. Observation-I: the UTGs of UEware are different from those of
the legitimate apps.
2. Observation-II: the UTGs of the same type of UEware are simi-
lar, while the UTGs of different types of UEware vary from each
other.

For the first observation, we have shown an underground loan
app in Figure laon app. Additionally, we select some official loan apps for comparison. We point out that UEware only implement partial functions (i.e., usury application) and ignore legal norms, which leads to considerable differences in UTG construction. 
<div align="center">
	<img src="./fig/loan.png" width="50%">
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">Loan app</div>
</div>


To demonstrate the second observation, we randomly select another underground loan app (with different Manifest). Although their runtime screenshots are different, they share a similar UTG (e.g., home page, loan apply, bank card check). Then we picked a underground gambling app to compare. Different from loans, the gambling app provides many game windows and a recharge window instead of loan apply. The services of these two types of apps are completely different, resulting in their UTG differences.
<div align="center">
	<img src="./fig/loan_2.png" width="70%">
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">Loan app #2</div>
</div>
<div align="center">
	<img src="./fig/gamble_1.png" width="70%">
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">Gamble app</div>
</div>
<div align="center">
	<img src="./fig/compare.png" width="70%">
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">UTG compare</div>
</div>

## System OverView

Based on the proposed approach, we design a system named DeUEDroid to detect the UEware via UTG. Specifically, DeUEDroid first
builds UTG for the training APKs, and then extracts features of
UTG. After that, it applies a machine learning method (i.e., self-
supervised representation learning) to train the classifier to detect
UEware. Figure 3 shows the architecture of DeUEDroid. There are
three modules, i.e., UTG Builder, UTG Feature Extractor and UEware
Detector, as follows:

1. **UTG Builder.** This module accepts Android APK files as the
input, and outputs the UTGs. It consists of two phases: GUI widget
identification and UI transition determination. 
2. **UTG Feature Extractor.** Based on the UTGs, this module com-
bines both GUI attributes and UTG topology together and out-
puts the UTG representation. Specifically, it leverages the MaskGAE with a 2-layer GCN  to embed
UTG. 
3. **UEware Detector.** Based on the UTG features, this module
leverages the self-supervised representation learning to train a
UEware classifier, which will be used to perform the detection.
<div align="center">
	<img src="./fig/overview.png" width="50%">
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">Overview</div>
</div>

## Dataset



List of the APPs used for evaluation
| **Dataset** | Component            | Setup Time | Detail | Number |
|:---------------|:----------------------------------|------------------:|--------------:|-------------------|
| OpenSource Dataset        | Self-developed           | July, 2022             | Self-developed for UTG        | 5            |1|
|         |  Real-World        | 2021- 2022             | site.leos.setter         | 1            |1|
|         |          |              | de.digisocken.antherrss         | 1            |1|
|         |          |             | org.woheller69.weather          | 1            |1|
| Ground-truth Dataset        | UEware           | June, 2022             | Gambling Game        | 470           |1|
|         |          |             | Porn          | 497            |1|
|         |          |             | Financial          | 300           |1|
|       | Legitimate Apps           | June, 2022             | --        | 831           |1|
| Large-scale Dataset        | Wild           | June-July, 2022             | App form website        | 13,460          |1|
|         | Appstore           | June-July, 2022             | App form Appstore        | 10,557          |1|
| **Total**       | --                               | --        | --    | 26,597               | --|
