## Contrak Foundry Example

This repository shows an example of using Contrak to track smart contract deployments done with Foundry.

### Install Foundry

Follow the installation guide inside of the [Foundry Book
](https://book.getfoundry.sh/getting-started/installation)
### Install the Contrak CLI

Install from NPM [@contrak/cli](https://www.npmjs.com/package/@contrak/cli)

```
npm i -g @contrak/cli
```

Test that the installation worked in your terminal.

```
contrak
```

### Environment setup

Set the environment variables in your deployment environment.

Contrak will automatically load any .env file in the directory you run the commands from. You can copy over the .env.example file and change the values to point to your Contrak server.

```
CONTRAK_URL=https://contrak.xyz // replace with your server url
CONTRAK_API_URL=https://contrak.xyz/api // replace with your server url
```

### Foundry Create

When deploying a contract using `forge create`, you want to use the `--json` parameter and pipe the results to `contrak connect-foundry`

Example of deploying the [default contract from the hello_foundry project from Foundry Book](https://book.getfoundry.sh/getting-started/first-steps)

Start the local network with anvil

```
anvil
```

then in another terminal run

```

forge create --json --private-key 0xac0974bec39a17e36ba4a6b4d238ff944bacb478cbed5efcae784d7bf4f2ff80 src/Counter.sol:Counter | contrak connect-foundry Counter 31337
```

Note the private key is the default key from the local network, you should never hard code private keys.

On success you should see an output in your terminal similar to the one below.

```
forgeOutput {
  deployer: '0xf39Fd6e51aad88F6F4ce6aB8827279cffFb92266',
  deployedTo: '0xa513E6E4b8f2a923D98304ec87F64353C4D5C853',
  transactionHash: '0x34178d4a5b6f5a9a505f9158f3cc8f64f9374bd6d9ea0218fa33651a137cc3da'
}
Contrak: Contract Connected
Sent Contract Details to:  https://contrak.xyz/api
```

### Viewing your Contracts

Once the create command has run, you can go to the `CONTRAK_URL` to view your smart contracts.

<img width="795" alt="image" src="https://github.com/NikitaVr/contrak-foundry-example/assets/10101970/994cb338-23c2-49bf-aea1-63c0f9c6f2d2">

