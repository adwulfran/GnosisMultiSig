### Easy way to deploy Gnosis multisig contract on any Ethereum Network

Create .env file
```bash
DEPLOYMENT_ACCOUNT_ADDRESS=0xb8..83
DEPLOYMENT_ACCOUNT_PRIVATE_KEY=67...14

RPC_URL=https://sokol.poa.network
OWNER_1=0xdd2BcC1e053aBB1DfA6c1F3D6C7842f57d61440F
OWNER_2=0xA5025FABA6E70B84F74e9b1113e5F7F4E7f4859f
OWNER_3=0x283C7b3D457FbfB53a903FB5312A1e48427044C1
REQUIRED=2

GET_RECEIPT_INTERVAL_IN_MILLISECONDS=3000
GAS_PRICE=1
```

```bash
npm install
node index.js
```


Example output:

```bash
➜  gnosis-deploy git:(master) ✗ node index.js
compling ./MultiSigGnosis.sol ...
compiled successfully ./MultiSigGnosis.sol
estimating gas...
gasLimit =  1714708
sending tx...
txHash 0x1b88f2e8df7240c11df7116282f5a8fb19d256b06a54dec72a9f245b920d1532
pending 3 seconds...
pending 6 seconds...
pending 9 seconds...
Deployed Multisig: 0xfAB8d14e8DE6cF567678a2f300A68EE5E54fF0a0

   Owners: 0xdd2BcC1e053aBB1DfA6c1F3D6C7842f57d61440F,0xA5025FABA6E70B84F74e9b1113e5F7F4E7f4859f,0x283C7b3D457FbfB53a903FB5312A1e48427044C1
   Required Signatures: 2

```


flow of transaction from command lines
~# node 
> var Web3 = require('web3');
> var web3 = new Web3(new Web3.providers.HttpProvider('https://ropsten.infura.io/yourapikey'));
> var privateKey = 'your-private-key';
> web3.eth.accounts.wallet.add("0x" + privateKey);
> web3.eth.accounts // check web3 account well imported
> var abi = [...];
> var MyContract = new web3.eth.Contract(abi, '0x3D694Eb73962BFDDCC4b795893588D8142030cbD');
> console.log(MyContract);
> MyContract.methods.getOwners().call({from : '0x5C7EB9331Fd719EEdeeb19802cB8de8F6c53a79C'}).then(receipt => { console.log(receipt) });
> MyContract.methods.addOwner("0xeC8F1C1d83377A6bAd02ff1aF49d9e4FDdBa01F8").send({from : '0x5C7EB9331Fd719EEdeeb19802cB8de8F6c53a79C', gas : 800000}).then(receipt => { console.log(receipt) });
> MyContract.methods.submitTransaction("0x3D694Eb73962BFDDCC4b795893588D8142030cbD",2, "0x").send({from : '0x5C7EB9331Fd719EEdeeb19802cB8de8F6c53a79C', gas : 800000}).then(receipt => { console.log(receipt) });
