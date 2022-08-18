# Guide on Mnemonic (seed phrase) to Keys and Addresses
A step-by-step guide on how mnemonic works (specifically on Cardano using `cardano-cli` and `cardano-wallet`), from deriving keys to using the address and signing transactions

## Prerequisites

### Install `cardano-node` and `cardano-cli`
1. Go to [IOHK - Cardano Node](https://github.com/input-output-hk/cardano-node) repository on Github
2. Scroll down to *Executables*, and download the binaries for your specific OS (MacOS, Linux, or Windows). For this demonstration, we're using node version 1.35.0
3. Extract and copy the files to `~/.local/bin-cardano/node-1.35.0/`

### Install 'cardano-wallet'
1. Go to [IOHK - Cardano Wallet](https://github.com/input-output-hk/cardano-wallet) repository on Github
2. Scroll down to *Latest releases* section, and choose [v2022-07-01](https://github.com/input-output-hk/cardano-wallet/releases/tag/v2022-07-01), because it is the `cardano-wallet` version that's compatible with node version 1.35.0
3. Download the binaries for your OS (MacOS, Linux, or Windows)
4. Extract and copy the files to `~/.local/bin-cardano/wallet-v2022-07-01/`

### Add binaries to `$PATH`
1. Edit `~/.zshrc` or `~/.bashrc`
2. Insert this `PATH` at the bottom
    ```bash
    ...
    # Path for cardano-node, cardano-cli, and cardano-wallet
    export PATH="$HOME/.local/bin-cardano/node-1.35.0:$PATH"
    export PATH="$HOME/.local/bin-cardano/wallet-v2022-07-01:$PATH"
    ```
3. **Note**: *there's some reduncancy with some files, such as `cardano-node` and `cardano-cli` exist in both directories. The order of `PATH` declaration will determine which file will be used. In this case, it will use the `cardano-wallet` directory.*
