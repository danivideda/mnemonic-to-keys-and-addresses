# Guide on Mnemonic / Seed Phrase, Keys, and Addresses on Cardano
A step-by-step guide on **how mnemonic works** (specifically on **Cardano** using `cardano-cli` and `cardano-wallet`), from deriving keys to using the address and signing transactions

**TABLE OF CONTENT**

- [Guide on Mnemonic / Seed Phrase, Keys, and Addresses on Cardano](#guide-on-mnemonic--seed-phrase-keys-and-addresses-on-cardano)
  - [✅ Prerequisites](#-prerequisites)
    - [Install `cardano-node` and `cardano-cli`](#install-cardano-node-and-cardano-cli)
    - [Install `cardano-wallet`](#install-cardano-wallet)
    - [Add directory to `$PATH`](#add-directory-to-path)
    - [Check if installed correctly](#check-if-installed-correctly)
  - [📝 Generate Mnemonic or Seed Phrase](#-generate-mnemonic-or-seed-phrase)
  - [🔑 Create and Derive Keys – *private, public, signing, and verify keys*](#-create-and-derive-keys--private-public-signing-and-verify-keys)
    - [Account Keys](#account-keys)
  - [🏠 Create Account Addresses – *testnet and mainnet*](#-create-account-addresses--testnet-and-mainnet)

## ✅ Prerequisites

### Install `cardano-node` and `cardano-cli`
1. Go to [IOHK - Cardano Node](https://github.com/input-output-hk/cardano-node) repository on Github
2. Scroll down to *Executables*, and download the binaries for your specific OS (MacOS, Linux, or Windows). For this demonstration, we're using node version 1.35.0
3. Extract and copy the files to `~/.local/bin-cardano/node-1.35.0/`

### Install `cardano-wallet`
1. Go to [IOHK - Cardano Wallet](https://github.com/input-output-hk/cardano-wallet) repository on Github
2. Scroll down to *Latest releases* section, and choose [v2022-07-01](https://github.com/input-output-hk/cardano-wallet/releases/tag/v2022-07-01), because it is the `cardano-wallet` version that's compatible with node version 1.35.0
3. Download the binaries for your OS (MacOS, Linux, or Windows)
4. Extract and copy the files to `~/.local/bin-cardano/wallet-v2022-07-01/`

### Add directory to `$PATH`
1. Edit `~/.zshrc` or `~/.bashrc`
2. Insert this `PATH` at the bottom
    ```bash
    ...
    # Path for cardano-node, cardano-cli, and cardano-wallet
    export PATH="$HOME/.local/bin-cardano/node-1.35.0:$PATH"
    export PATH="$HOME/.local/bin-cardano/wallet-v2022-07-01:$PATH"
    ```
3. **Note**: *there's some reduncancy with some files, such as `cardano-node` and `cardano-cli` exist in both directories. The order of `PATH` declaration will determine which file will be used. In this case, it will use the `cardano-wallet` directory.*

### Check if installed correctly
1. Open new terminal session
2. Check the version for each command
    ```bash
    $ cardano-node --version
    # cardano-node 1.35.0 - darwin-x86_64 - ghc-8.10
    # git rev 9f1d7dc163ee66410d912e48509d6a2300cfa68a

    $ cardano-cli --version
    # cardano-cli 1.35.0 - darwin-x86_64 - ghc-8.10
    # git rev 9f1d7dc163ee66410d912e48509d6a2300cfa68a

    $ cardano-wallet version
    # v2022-07-01 (git revision: c0ece6ad1868682b074708ffb810bdc2ea96934f)
    ```
3. **Note**: *for Mac users, if you encounter any Security issues, open **Apple > System Preferences > Security & Privacy**, and click 'Allow' when prompted*

## 📝 Generate Mnemonic or Seed Phrase
1. Generate 24 seed phrase using. This is done locally and doesn't require internet connection
    ```bash
    $ cardano-wallet recovery-phrase generate --size 24 | tee mnemonic.txt
    ```

    <img src="img/generate-seed.png" style="width:80%;">

2. Convert the seed phrase into Master Root Key 
    ```bash
    $ cardano-wallet key from-recovery-phrase Shelley < mnemonic.txt | tee keys/root.xprv
    ```
    <img src="img/root.png" style="width:80%;">

## 🔑 Create and Derive Keys – *private, public, signing, and verify keys*

Cardano uses [Hierarchical Deterministic Wallet](https://input-output-hk.github.io/cardano-wallet/concepts/hierarchical-deterministic-wallets)

### Account Keys
One seed phrase can generates many accounts and use them seperately.

<img src="img/accounts-eternl.png" style="width:80%;">

When using Eternl wallet, you can see the HD Wallets deriviation path on each account; `(m/1852'/1815'/0'), (m/1852'/1815'/1'), and (m/1852'/1815'/2')`

1. Derive from Master Root Key into Account #0

## 🏠 Create Account Addresses – *testnet and mainnet*