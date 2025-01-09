### Bonkcoin Full Node Build Guide (README)

Bonkcoin is a custom cryptocurrency based on the Litecoin codebase. This guide explains how to build a Bonkcoin full node on Linux.

---

### **Prerequisites**
1. A server or virtual machine running Ubuntu 20.04 or later.
2. Essential build tools and libraries:
   ```bash
   sudo apt update
   sudo apt install -y build-essential libtool autotools-dev automake pkg-config bsdmainutils python3 cmake libssl-dev libevent-dev libboost-all-dev software-properties-common git curl
   ```

---

### **Clone the Repository**
```bash
git clone https://github.com/bonkcoins/bonkcoin.git
cd bonkcoin
```

---

### **Prepare the Build Environment**

#### **Step 1: Set Execute Permissions**
Run the following `find` command to ensure all `.sh` files are executable:
```bash
find . -type f -name "*.sh" -exec chmod +x {} \;
```

#### **Step 2: Generate the Configuration Files**
```bash
./autogen.sh
```

---

### **Build the Dependencies**

1. Navigate to the `depends` directory:
   ```bash
   cd depends
   ```

2. Build the dependencies:
   ```bash
   chmod +x config.guess
   chmod +x config.sub
   ./config.guess
   ./config.sub
   make -j$(nproc)
   ```

3. Go back to the root directory:
   ```bash
   cd ..
   ```

---

### **Configure and Build Bonkcoin**

1. Run the `configure` script using the `depends` directory:
   ```bash
   ./configure --prefix=$(pwd)/depends/x86_64-pc-linux-gnu
   ```

2. Compile the source code:
   ```bash
   make -j$(nproc)
   ```

3. Optionally, run tests to verify the build:
   ```bash
   make check
   ```

4. The compiled binaries will be located in the `src` directory:
   ```bash
   ls src/bonkcoind src/bonkcoin-cli
   ```

---

### **Run a Full Node**

1. Create the Bonkcoin data directory:
   ```bash
   mkdir -p ~/.bonkcoin
   ```

2. Add a `bonkcoin.conf` configuration file:
   ```bash
   nano ~/.bonkcoin/bonkcoin.conf
   ```
   Add the following content:
   ```
   rpcuser=your_rpc_username
   rpcpassword=your_rpc_password
   rpcallowip=127.0.0.1
   listen=1
   server=1
   daemon=1
   ```
   Save and exit (`Ctrl+O`, `Ctrl+X`).

3. Start the Bonkcoin daemon:
   ```bash
   ./src/bonkcoind -daemon
   ```

4. Check the status:
   ```bash
   ./src/bonkcoin-cli getblockchaininfo
   ```

---

### **Additional Links**
- [Bonkcoin Website](https://bonkpow.com)
- [Explorer](https://explore.bonkpow.com)

---

### **Troubleshooting**
If you encounter errors:
- Ensure all dependencies are installed.
- Verify file permissions using:
  ```bash
  find . -type f -name "*.sh" -exec chmod +x {} \;
  ```
- If a `Makefile` is missing, rerun `./autogen.sh` and `./configure`.

Feel free to report issues on the GitHub repository.
