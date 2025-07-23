# Documentation – Project Workflow  
*Date:* _As of: July 23th, 2025_  
*Author:* Erik Ziechmann

## Initial MRI Setup  
_only required once at the beginning_

1. Open Device Manager and find the COM port  
2. Start PuTTY using the COM port (e.g., COM5)  
3. Enter `ip addr show`  
4. The `inet` address shows the board's IP address  

When opening this address in a browser, a configuration menu appears where static IPs can be set

1. In `marcos_client/` rename `local_config.py.example` → `local_config.py`
2. Set the found IP address (e.g., 172.16.8.107)
3. Comment out `fpa_clk_freq_MHz = 125` and replace with `122.88`
4. `grad_board` must be `ocra1`
5. In `marcos_experiments/` rename `mri_config.py.examples` → `mri_config.py`
6. `grad_max_Hz_per_m = 10.9e6` must be set, comment out all others
7. In `marcos_experiments/` rename `external.py.examples` → `external.py`
8. Clone `flocra_pulseq` from git (https://github.com/catkira/flocra-pulseq.git). Use `pulseq_1.4` version

## Routine MRI Setup  
_each time before using the MRI_

1. Open terminal  
2. Select Ubuntu (top menu)  
3. Run the following commands  
- `cd git`  
- `cd marcos_pack/` (https://github.com/catkira/marcos_pack.git)  
- `cd marcos_extras/` (https://github.com/vnegnev/marcos_extras.git)  
- `./marcos_setup.sh 172.16.8.107 rp-122` (old: 172.16.8.254)  
- Copy and execute the displayed command

4. Open VS Code – now code execution is possible  
5. (Optional: `cd git`, `git remote`)

**Important:** on first setup and access via console  
`ssh-copy-id root@172.16.8.107` (password is `root`)

## Code Setup

1. Open Visual Studio Code  
2. Open marcos_client (https://github.com/catkira/marcos_client.git)  
3. Set IP address to the board address (from initial setup)  
4. Open test loopback code → verify results with loop (RX1 and TX physically connected)  
5. Now sequences can be run

## Required Libraries

numpy  
matplotlib  
msgpack  
PyQt5  
scipy  
external
