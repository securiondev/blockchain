# Safe ERC-4337 Integration Guide

Production-ready examples for integrating Safe smart accounts with ERC-4337 Account Abstraction.

## Features

- ERC-4337 Account Abstraction
- Safe4337Pack integration
- Bundler support
- Paymaster support
- UserOperation examples
- Solidity validation examples

## Installation

```bash
npm install @safe-global/relay-kit
npm install @safe-global/api-kit
npm install viem
```

## Initialize Safe4337Pack

```ts
import { Safe4337Pack } from '@safe-global/relay-kit'

const safe4337Pack = await Safe4337Pack.init({
  provider: RPC_URL,
  signer: PRIVATE_KEY,
  bundlerUrl: BUNDLER_URL,
  options: {
    owners: [SIGNER_ADDRESS],
    threshold: 1
  }
})
```

## Create UserOperation

```ts
const transaction = {
  to: '0xTargetAddress',
  data: '0x',
  value: '0'
}

const safeOperation =
  await safe4337Pack.createTransaction({
    transactions: [transaction]
  })
```

## Execute Operation

```ts
const userOperationHash =
  await safe4337Pack.executeTransaction({
    executable: signedSafeOperation
  })
```

## References

- https://docs.safe.global/advanced/erc-4337/4337-safe
- https://docs.erc4337.io/core-standards/erc-4337.html

## License

MIT
