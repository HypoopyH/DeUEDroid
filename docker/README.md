# Docker Usage
In order to allow users to use our system (DeUEDroid) more conveniently, we have built a Docker image.

## Download
Users can download images from docker hub by themselves. Docker image Tag: `hypoopyh/deuedroid`. 

## Build UTG (UI-Transition-Graph)
We synthesize the build process into one script (`run.py` and `run_static.sh`) for ease of use, and we show the UTG build process as a demo.

```bash
#build UTG for apps in /root/KueiHsing/test, and output the result in /root/KueiHsing/output
/etc/init.d/mysql start  # make sure mysql is running
cd /root/KueiHsing/StaticAnalysis
python3 run.py --ApkFolder /root/KueiHsing/test --Output /root/KueiHsing/output # run UTG builder 
```

If there are some special needs, such as overtime modification, changing the sdk path of a higher version, etc., you can modify the script by yourself.

## MaskGAE detector
We synthesize the detection model trained on the ground-truth dataset (1700 apps). 

```bash
# preprocess the static analysis results
# the result locate in /MaskGAE/raw/..
python3 preprocess.py
# run detector 
python3 demo.py
```
We only provide the detector demonstration in the script, and if users need it, they can load our model to fulfill other needs. 

## Resources
The dataset is uploaded in One Drive. 
