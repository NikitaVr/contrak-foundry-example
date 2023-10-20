## Contrak Foundry Example

This repository shows an example of using Contrak to track smart contract deployments done with Foundry.

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

### Viewing your Contracts

Once the create command has run, you can go to the `CONTRAK_URL` to view your smart contracts.
