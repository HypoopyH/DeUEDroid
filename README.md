
## Motivating Example
To perform an effective large-scale detection, we propose an UEware detection approach based on the UTG similarity. Our approach is based on two key observations:
1. Observation-I: the UTGs of UEware are different from those of
the normal apps.
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
    padding: 2px;">UTG comparision</div>
</div>


## Dataset

https://1drv.ms/u/s!AleQ4_D215AMbPVD4pyE37oligM?e=n5XXAl

List of the APPs used for evaluation
| **Dataset** | Component            | Setup Time | Detail | Number |
|:---------------|:----------------------------------|------------------:|--------------:|-------------------|
| OpenSource Dataset        | Self-developed           | July, 2022             | Self-developed for UTG        | 5            |1|
|         |  Real-World        | 2021- 2022             | site.leos.setter         | 1            |1|
|         |          |              | de.digisocken.antherrss         | 1            |1|
|         |          |             | org.woheller69.weather          | 1            |1|
|         |          |             |  net.gsantner.dandelior          | 1            |1|
|         |          |             |  com.github.dfa.diaspora_android         | 1            |1|
|         |          |             |  com.chao.app          | 1            |1|
|         |          |             |  de.storchp.opentracks.osmplugin         | 1            |1|
|         |          |             |  com.kylecorry.trail_sense         | 1            |1|
|         |          |             |  org.woheller69.arity         | 1            |1|
|         |          |             |  ademar.bitac         | 1            |1|
| Ground-truth Dataset        | UEware           | June, 2022             | Gambling Game        | 310           |1|
|         |          |             | Porn          | 341            |1|
|         |          |             | Financial          | 197           |1|
|       | Normal Apps           | June, 2022             | --        | 852           |1|
| Large-scale Dataset        | Wild           | June-July, 2022             | App form website        | 13,460          |1|
|         | Appstore           | June-July, 2022             | App form Appstore        | 10,557          |1|
| **Total**       | --                               | --        | --    | 25,732               | --|
