Perfect! Here's a **clean, step-by-step tutorial** you can directly copy into your GitHub repository README or documentation to help users fix the `sim_vehicle.py: command not found` issue and set up their ArduPilot SITL environment properly:

---

# 🚁 ArduPilot SITL Setup Guide (Fix `sim_vehicle.py: command not found`)

This guide walks you through setting up ArduPilot’s Software In The Loop (SITL) simulation and fixing the common issue:

> `sim_vehicle.py: command not found`

---

## ✅ Prerequisites

* Ubuntu 20.04 or later (tested on Ubuntu 22.04)
* Git installed
* Python 3.x installed
* Internet connection

---

## 🛠️ Step-by-Step Instructions

### 1. Clone the ArduPilot Repository

```bash
git clone https://github.com/ArduPilot/ardupilot.git
cd ardupilot
git submodule update --init --recursive
```

---

### 2. Install Required Dependencies

```bash
Tools/environment_install/install-prereqs-ubuntu.sh -y
. ~/.profile
```

This installs all system packages and updates your environment variables.

---

### 3. Setup the Environment for ArduPilot

Each time you want to use `sim_vehicle.py`, **you must source this file**:

```bash
. Tools/completion/bash_completion
```

To make this permanent, add it to your `.bashrc` file.

---

### 4. Add sim\_vehicle.py to Your PATH

#### Step 4.1: Open `.bashrc` in a text editor

```bash
nano ~/.bashrc
```

#### Step 4.2: Add the following line to the end of the file

```bash
export PATH=$PATH:$HOME/ardupilot/Tools/autotest
```

#### Step 4.3: Save and close the file

* Press `Ctrl + O`, then `Enter` to save
* Press `Ctrl + X` to exit

#### Step 4.4: Reload `.bashrc`

```bash
source ~/.bashrc
```

---

### 5. Build the Copter for SITL

```bash
./waf configure --board sitl
./waf copter
```

---

### 6. Run the Simulator

You can now run the SITL simulator with GUI:

```bash
sim_vehicle.py --console --map -w
```

✅ `--console` opens MAVProxy
✅ `--map` opens a live map
✅ `-w` wipes previous parameters (only needed on first run)

---

## 🧠 Notes

* Always run the simulation from the `ArduCopter` directory:

  ```bash
  cd ~/ardupilot/ArduCopter
  sim_vehicle.py --console --map
  ```
* For Plane or Rover:

  ```bash
  cd ~/ardupilot/ArduPlane     # or ArduRover
  sim_vehicle.py --console --map
  ```

---

## 📎 Sample Output (Success)

If successful, you will see:

```
...
Starting SITL
Running: ArduCopter.elf ...
Connect /dev/pts/2
...
```

---


