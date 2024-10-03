cara melakukan verifikasi smart contract dengan etherscan :

1. deploy smart contract ke jaringan evm yang dipilih
2. setelah selesai dan mendapatkan contract addressnya
3. isi etherscan apikey kedalam setting configurasinya

4. jalankan dengan command "npx hardhat verify --network betherance "contract address" "parameter"", contoh dalam case ini memakai lock contract yang di deploy di minato testnet

```
npx hardhat verify --network minato "0x0A4aA89AC1c33AEED5CDce61607b2C0d7DDffB29" "1893456000"
```

contoh config

```javascript
require('@nomicfoundation/hardhat-toolbox');
require('@nomicfoundation/hardhat-verify');

/** @type import('hardhat/config').HardhatUserConfig */
module.exports = {
  solidity: '0.8.27',
  networks: {
    holesky: {
      url: 'https://ethereum-holesky.publicnode.com/', // URL RPC untuk jaringan BSC Testnet
      accounts: [`xxxx`], // Mengimpor private key dari variabel lingkungan
    },
    goerli: {
      url: 'https://eth-goerli.g.alchemy.com/v2/YOUR_ALCHEMY_KEY', // URL RPC untuk Ethereum Goerli Testnet
      accounts: [`xxxx`], // Mengimpor private key dari variabel lingkungan
    },
    'eth-sepolia': {
      url: 'https://rpc.sepolia.org',
      accounts: [`xxxx`], // Mengimpor private key dari variabel lingkungan
    },
    minato: {
      url: 'https://rpc.minato.soneium.org/',
      chainId: 1946,
      accounts: [`xxxx`], // Mengimpor private key dari variabel lingkungan
    },
    betherance: {
      url: 'https://rpc.bethscan.io/',
      chainId: 1605,
      accounts: [`xxxx`], // Mengimpor private key dari variabel lingkungan
    },
  },
  etherscan: {
    // Your API key for Etherscan
    // Obtain one at https://etherscan.io/
    apiKey: {
      minato: 'empty',
      betherance: 'empty',
    },
    customChains: [
      {
        network: 'minato',
        chainId: 1946,
        urls: {
          apiURL: 'https://explorer-testnet.soneium.org/api',
          browserURL: 'https://explorer-testnet.soneium.org',
        },
      },
      {
        network: 'betherance',
        chainId: 1605,
        urls: {
          apiURL: 'https://api.bethscan.io/api',
          browserURL: 'https://api.bethscan.io/',
        },
      },
    ],
    // apiKey: 'JDSM45NIE986J2VIX9H179PFFAFHSK9KFE',
  },
};
```
