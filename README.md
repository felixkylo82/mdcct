# MDCCT

### Original code 
Linux BURST coin miner/optimizer (untouched original code)<br>
Author: Niksa Franceschi <niksa.franceschi@gmail.com><br>
Burst for donations: BURST-RQW7-3HNW-627D-3GAEV<br>
<br>
Linux miner/plotter/plot optimizer by dcct / Markus Tervooren <info@bchain.info><br>
Burst: BURST-R5LP-KEL9-UYLG-GFG6T<br>

### Plot Generator Optimized for SSE4 / AVX2
Modified by https://github.com/Mirkic7/mdcct
Linux BURST coin plot generator optimized for SSE4 / AVX2<br>
Speed gain of ~2x using SSE4 core instead of original<br>
AVX2 not tested (report results!)<br>
<br>
Modified using BurstSoftware code: https://github.com/BurstTools/BurstSoftware <br>
by Cerr Janror <cerr.janror@gmail.com><br>
Burst: BURST-LNVN-5M4L-S9KP-H5AAC<br>

### Miner Optimized for SSE4
Modified by https://github.com/felixkylo82/mdcct.git <br>
by Felix LO <kuiyipl@acm.org><br>
Burst: BURST-VFCU-33N9-9GKF-34THX<br>

### Installing
    git clone https://github.com/felixkylo82/mdcct.git
    cd mdcct
    make

Installation may break on AVX2 code (depending on compiler), but it is separate binary.<br>

Async writer can speed up plotting due to not waiting to write to disk.<br>
This is especially true with slower disks and larger stagger sizes.<br>
However, it will use 2x memory.<br>

### Plot Generator Usage
###### For SSE4
```bash
./plot -k NUMERICACCOUNTID [ -x CORE ] [-d DIRECTORY] [-s STARTNONCE] [-n NONCES] [-m STAGGERSIZE] [-t THREADS] -a
```
     CORE:
       0 - default core
       1 - SSE4 core
     -a = ASYNC writer mode (will use 2x memory!)

###### For AVX2
```bash
./plotavx2 -k NUMERICACCOUNTID [ -x CORE ] [-d DIRECTORY] [-s STARTNONCE] [-n NONCES] [-m STAGGERSIZE] [-t THREADS] -a
```
      CORE:
        0 - default core
        1 - SSE4 core
        2 - AVX2 core
       -a = ASYNC writer mode (will use 2x memory!)
 
###### Not specifying -x option will default to original dcct ploter

### Miner Usage
###### For SSE4 Pool Mining
```bash
./mine_pool_all HOST:PORT DIRECTORY [DIRECTORY...]
```
 
###### One thread is dedicated, under each directory, to read plots and to find better deadlines
