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
