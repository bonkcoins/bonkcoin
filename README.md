```markdown
# BonkCoin Full Node Build Guide

## **Prerequisites**
Ensure you have the following dependencies installed:
```bash
sudo apt update
sudo apt install -y build-essential libtool autotools-dev automake pkg-config bsdmainutils python3 cmake curl git
sudo apt install -y libssl-dev libevent-dev libboost-all-dev
sudo apt install -y software-properties-common
sudo add-apt-repository ppa:bitcoin/bitcoin
sudo apt update
sudo apt install -y libdb4.8-dev libdb4.8++-dev
```

---

## **Clone the BonkCoin Repository**
```bash
git clone https://github.com/bonkcoins/bonkcoin.git
cd bonkcoin
```

---

## **Build Dependencies**
Navigate to the `depends` directory and build the required dependencies:
```bash
cd depends
chmod +x config.guess config.sub
make -j$(nproc)
```

---

## **Build BonkCoin**
1. Return to the root directory:
   ```bash
   cd ..
   ```

2. Run the autogen script:
   ```bash
   ./autogen.sh
   ```

3. Configure the build to use the dependencies:
   ```bash
   ./configure --prefix=`pwd`/depends/x86_64-pc-linux-gnu
   ```

4. Build BonkCoin:
   ```bash
   make -j$(nproc)
   ```

---

## **Run the BonkCoin Node**
1. Start the BonkCoin daemon:
   ```bash
   ./src/bonkcoind
   ```

2. To check the node status, use the CLI:
   ```bash
   ./src/bonkcoin-cli getblockchaininfo
   ```

---

## **Important Links**
- **Website**: [https://bonkpow.com](https://bonkpow.com)  
- **Explorer**: [https://explore.bonkpow.com](https://explore.bonkpow.com)
```
