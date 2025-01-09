# BonkCoin

BonkCoin is a secure and decentralized cryptocurrency designed for fast and efficient peer-to-peer transactions. It uses the Scrypt algorithm and supports Proof-of-Work (PoW) mining. 

**Website:** [BonkCoin Official Website](https://bonkpow.com)  
**Explorer:** [BonkCoin Blockchain Explorer](https://explore.bonkpow.com)

---

## Features

- **Scrypt Algorithm:** Optimized for secure and efficient mining.
- **Fast Transactions:** Designed for quick and reliable payments.
- **Open Source:** Fully transparent and customizable.

---

## How to Build a Full Node

Follow these steps to compile and run a BonkCoin full node using the `depends` directory.

### Prerequisites

- **Operating System:** Ubuntu 20.04+ (or similar Linux distributions)
- **Tools and Dependencies:**
  - `build-essential`
  - `autoconf`
  - `automake`
  - `libtool`
  - `pkg-config`
  - `bison`
  - `g++`
  - `make`

Install them with:
```bash
sudo apt-get update
sudo apt-get install -y build-essential autoconf automake libtool pkg-config bison g++ make
```

### Step-by-Step Guide

1. **Clone the Repository**
   ```bash
   git clone https://github.com/bonkcoins/bonkcoin.git
   cd bonkcoin
   ```

2. **Build the Dependencies**
   Navigate to the `depends` directory and compile the dependencies:
   ```bash
   cd depends
   make -j$(nproc)
   cd ..
   ```

3. **Configure the Build**
   Use the `depends` output to set up the build environment:
   ```bash
   ./autogen.sh
   ./configure --prefix=$(pwd)/depends/x86_64-pc-linux-gnu
   ```

4. **Compile BonkCoin**
   Start the build process:
   ```bash
   make -j$(nproc)
   ```

5. **Run the Full Node**
   After compilation, you can start the node:
   ```bash
   ./src/bonkcoind
   ```

6. **Configuration**
   Create a configuration file at `~/.bonkcoin/bonkcoin.conf`:
   ```conf
   rpcuser=yourrpcuser
   rpcpassword=yourrpcpassword
   daemon=1
   server=1
   ```
   Start the node again:
   ```bash
   ./src/bonkcoind -daemon
   ```

---

## Mining with BonkCoin

BonkCoin uses the Scrypt algorithm for mining. You can connect your miners to your full node or use an external pool. Explore blocks, transactions, and addresses with our [Blockchain Explorer](https://explore.bonkpow.com).

---

## Resources

- **Official Website:** [https://bonkpow.com](https://bonkpow.com)  
- **Explorer:** [https://explore.bonkpow.com](https://explore.bonkpow.com)

---

Feel free to contribute or submit issues. Happy mining!
