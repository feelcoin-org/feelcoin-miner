# Feelcoin Miner

Official CPU miner for **Feelcoin (FEEL)**.

**In Feels We Trust.**

Feelcoin Miner is based on the open-source XMRig mining engine and includes
Feelcoin-specific support for:

- RandomX (`rx/0`)
- Native FEEL wallet addresses
- Official Feelcoin pool defaults
- TLS pool mining
- Direct daemon solo mining
- Feelcoin post-block-590 treasury coinbase parsing
- 0% default upstream donation

## Quick Start

### Pool mining

./feelcoin-miner \
  --wallet YOUR_FEEL_ADDRESS \
  --worker YOUR_WORKER_NAME

Default TLS pool:

pool.feelcoin.org:4244

The official pool uses PPLNS and a 0.5% pool fee.

### Direct solo mining

./feelcoin-miner \
  --solo \
  --wallet YOUR_FEEL_ADDRESS

Default local daemon RPC:

127.0.0.1:35781

Direct daemon solo mining has no pool fee.

Do not expose your daemon RPC port publicly.

## Useful options

--wallet=ADDRESS
--worker=NAME
--solo
--threads=N
--print-time=N
--no-color

## Network

- Coin: Feelcoin
- Ticker: FEEL
- Proof of Work: RandomX
- Target block time: 120 seconds
- Standard pool: pool.feelcoin.org:4242
- TLS pool: pool.feelcoin.org:4244
- Daemon P2P: 35780
- Daemon RPC: 35781
- Daemon ZMQ: 35782

## Wallet validation

--wallet validates CryptoNote Base58 encoding and checksum and accepts
Feelcoin mainnet prefixes:

- 84 standard
- 85 integrated
- 86 subaddress

## Transparency

Feelcoin Miner does not enable an automatic developer donation.

The upstream XMRig donation framework remains present because this project
is derived from XMRig, but Feelcoin Miner's default donation level is 0%.

## Project links

- Website: https://feelcoin.org
- Pool: https://pool.feelcoin.org
- Explorer: https://explorer.feelcoin.org
- Web Wallet: https://wallet.feelcoin.org
- Paper Wallet: https://paper.feelcoin.org
- GitHub: https://github.com/feelcoin-org

## License and upstream attribution

Feelcoin Miner is derived from XMRig:
https://github.com/xmrig/xmrig

The upstream project and contributors retain their respective copyrights.

Feelcoin-specific modifications are maintained by the Feelcoin Project.

This software remains licensed under the GNU General Public License,
version 3 or later. See LICENSE.

The Feelcoin Project does not claim authorship of upstream XMRig code or
third-party components.


## Install Feelcoin Miner

The official prebuilt release currently targets **Linux x86_64** and was built and tested on Ubuntu 26.04.1.

### Download the official release

Download:

- `feelcoin-miner-v0.1.0-linux-x64.tar.gz`
- `feelcoin-miner-v0.1.0-linux-x64.sha256`

from the official release:

https://github.com/feelcoin-org/feelcoin-miner/releases/tag/v0.1.0

Verify the download before running it:

```bash
sha256sum -c feelcoin-miner-v0.1.0-linux-x64.sha256
```

Published SHA-256:

```text
82881827d445eba6009b11f377e9c17aa9b0c2fd2b9a7e4378a5f8c28818615e
```

Extract and run:

```bash
tar -xzf feelcoin-miner-v0.1.0-linux-x64.tar.gz
cd feelcoin-miner-v0.1.0-linux-x64
chmod +x feelcoin-miner
```

### Pool mining

```bash
./feelcoin-miner \
  --wallet YOUR_FEELCOIN_WALLET_ADDRESS \
  --worker YOUR_WORKER_NAME
```

The native Feelcoin Miner uses the official TLS pool configuration by default.

Official pool:

```text
pool.feelcoin.org:4244
```

### Direct solo mining

Run a local `feelcoind` node first, keeping RPC bound to localhost.

Then start:

```bash
./feelcoin-miner \
  --solo \
  --wallet YOUR_FEELCOIN_WALLET_ADDRESS
```

Direct daemon solo mining has **0% pool fee**.

### Custom daemon address

By default, `--solo` connects to the local Feelcoin daemon at:

```text
127.0.0.1:35781
```

To mine through a Feelcoin daemon running at another address or port:

```bash
./feelcoin-miner --daemon --url YOUR_DAEMON_IP:35781 --wallet YOUR_FEELCOIN_WALLET_ADDRESS
```

Example on a private network:

```bash
./feelcoin-miner --daemon --url 192.168.1.123:8197 --wallet YOUR_FEELCOIN_WALLET_ADDRESS
```

`-o` is intended for pool / Stratum connections. For direct daemon mining, use `--daemon --url`.

For security, do not expose the daemon RPC port directly to the public Internet.


## Build from Source

Install the build dependencies on Ubuntu:

```bash
sudo apt update
sudo apt install -y \
  git \
  build-essential \
  cmake \
  libuv1-dev \
  libssl-dev \
  libhwloc-dev
```

Clone the repository:

```bash
git clone https://github.com/feelcoin-org/feelcoin-miner.git
cd feelcoin-miner
git checkout v0.1.0
```

Build the CPU miner:

```bash
mkdir -p build
cd build

cmake .. \
  -DWITH_OPENCL=OFF \
  -DWITH_CUDA=OFF

make -j$(nproc)
```

Verify the binary:

```bash
./feelcoin-miner --version
```

## Transparency

Feelcoin Miner is based on the open-source XMRig codebase and retains the applicable upstream attribution and GPLv3 licensing requirements.

Feelcoin-specific additions include native FEEL wallet validation, Feelcoin pool defaults, direct daemon solo mining support and Feelcoin block-template handling.

The default upstream donation level is **0%**.

There is no hidden automatic developer fee in Feelcoin Miner.
