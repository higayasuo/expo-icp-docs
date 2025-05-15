# Advanced Setup

## Deploying Canisters for Playground

The playground environment is a testing environment that simulates the Internet Computer network. It's useful for testing your application before deploying to the mainnet.

To deploy Canisters to the playground, execute the following command:

```bash
npm run dfx:deploy:playground
```

**Important Notes**
- The playground environment is separate from your local development environment
- Changes in the playground don't affect your local development
- Playground deployments are temporary and may be cleared periodically
- Make sure you have sufficient cycles in your playground identity

## Preparation Steps for ICP Mainnet (ic) Deployment

Before deploying to the Internet Computer mainnet, you need to set up your development identity and obtain cycles. Follow these steps:

1. Create and switch to a development identity

```bash
dfx identity new dev
dfx identity use dev
```

2. Get your account's ledger account ID

```bash
dfx ledger account-id
```

3. Send ICP tokens to your ledger account ID

You can obtain ICP tokens from an exchange. If you are using an exchange, initiate a withdrawal transaction, then enter the ledger account ID as the "destination" address to send ICP tokens to.

4. Check your ICP balance

```bash
dfx ledger balance --network=ic
```

5. Convert ICP into cycles

Replace `AMOUNT` with the number of ICP tokens you want to convert into cycles:

```bash
dfx cycles convert --amount AMOUNT --network=ic
```

6. Confirm your cycles balance

```bash
dfx cycles balance --network=ic
```

**Important Notes**

- Make sure you have enough ICP tokens in your account before converting to cycles.
- The conversion rate from ICP to cycles is fixed and determined by the Internet Computer protocol.
- You can check your cycles balance at any time using `dfx cycles balance --network=ic`.
- For more information about cycles and resource consumption, see the [Internet Computer documentation](https://internetcomputer.org/docs/building-apps/getting-started/tokens-and-cycles).
- For detailed instructions on obtaining cycles, see the [Obtaining cycles](https://internetcomputer.org/docs/building-apps/getting-started/tokens-and-cycles#obtaining-cycles) section of the Internet Computer documentation.

## Backup and Restore Developer's Private Key

It's important to backup your developer identity's private key to prevent loss of access to your canisters. This is especially crucial when deploying to the mainnet.

### Export Private Key

```bash
dfx identity export dev > dev.pem
```

This command saves the private key of the dev identity in PEM format to the dev.pem file.

### Import Private Key

```bash
dfx identity import dev dev.pem
```

This imports the private key from the exported PEM file and registers it as the dev identity.

**Important Notes**

- You will be prompted for a passphrase during import
- The passphrase must be at least 8 characters long
- Store your passphrase securely and don't forget it
- The PEM file contains sensitive private key data and must be stored securely
- It is recommended to safely delete the PEM file after successful import
- Keep your private key backup in a secure location, such as an encrypted storage device

## Deploying Canisters for IC

The Internet Computer (IC) is the mainnet network where your application will be publicly accessible. To deploy Canisters to the IC, execute the following command:

```bash
npm run dfx:deploy:ic
```

This command performs the following operations:

1. Builds all Canisters (internet-identity, ii-integration, expo-starter-frontend, expo-starter-backend)
2. Installs the built Canisters to the IC mainnet

**Important Notes**

- Deployment may take several minutes
- Mainnet deployment requires cycles for operation
- Make sure you have sufficient cycles before deployment
- The deployment is permanent and will be publicly accessible
- Consider testing thoroughly in playground or local environment first
- Monitor your cycles balance after deployment to ensure continued operation

