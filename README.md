# CUDA miner (solo)
## Setup

```bash
apt install libcurl4-openssl-dev git cmake -y
```

## Usage
### Linux
[Download the latest files](https://github.com/geiccobs/upow-gpu/releases/latest), you'll need just `cuda`.

### Windows
[Download the latest files](https://github.com/geiccobs/upow-gpu/releases/latest), you'll need `cuda.exe` and all the `.dll` files.

### mmpOS
[Download the latest files](https://github.com/ddobreff/mmpos/releases/latest), you'll need `export_CUDA-uPoW.json` to initially install the custom miner.  
For future updates you'll need to update your miner profile custom URL with `upow-cuda-mmpos_VERSION.tar.gz`  

### Instructions
Use `./cuda --help` (or `cuda.exe --help` in Windows) to see the full list of arguments.  
Let's look at them:
- `--address` - your wallet address (learn about [multi-address support](#multiple-addresses))
- `--silent` - `(def: false)` don't print anything to stdout
- `--verbose` - `(def: false)` don't clear stdout after each share (useful for debugging)
- `--file` - `(def: false)` send `--verbose` stdout to `logs.txt` (useful for debugging)
- `--device` - `(def: 1)` max GPU device ID (learn about [multi-GPU support](#multiple-gpus))
- `--threads` - `(def: automatic)` number of threads related to GPUs
- `--blocks` - `(def: automatic)` number of blocks related to GPUs

### Platforms
This miner is tested on both Linux and Windows (WSL 2).  
It works on Windows, but hashrate displaying might be currently broken.  
Obviously it is working only on NVIDIA GPUs.

#### Having problems with libjson-c?
Please remember to use sudo before commands if required by your environment.

```bash
git clone https://github.com/json-c/json-c.git # clone the source code
cd json-c # go to the source code directory
mkdir build && cd build # create a build directory
cmake .. && make # build the source code
make install # install the library

cd ../.. # go back to the root directory
rm -rf json-c # remove the source code
```

## Discussed topics
### Multiple addresses
Multi-address support is available, you can use it by setting `--address` parameter to a comma-separated list of addresses.

Here's an example:
```bash
./cuda --address YOUR_ADDRESS,ADDRESS_2,ADDRESS_3
```

### Multiple GPUs
You can use multiple GPUs by setting `--device` parameter to any int, it will be the maximum device ID used by the miner.
If you want to use all the GPUs available on your machine, get the last device id listed in `nvidia-smi -L` + 1, every GPU with lower ID will be used.

### Fee
A mining fee is currently present and managed accurately ensuring that everyone who uses the miner with a proper setup will be extremely profitable (please, check the blockchain difficulty before considering to get a proper mining setup).  
Although with this miner you'll be profitable just by selling at floor price, I'd suggest to hold and eventually stake coins to create passive income, learn more at https://upow.ai/learn.

## Questions
I won't provide help for any kind of topic already explained here.  
If there are any doubts on anything, you're always free to contact me at https://t.me/ostaggio, but please get to the point.
