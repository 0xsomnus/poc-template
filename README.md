# Proof of Concept Template

This is a template for testing proof of concepts and recording vulnerability reports.

> NOTICE: This template assumes foundry is installed.
>
> See installation instructions [here](https://book.getfoundry.sh/getting-started/installation).

[PoC Contract](./src/PoC.sol)

[PoC Test](./test/PoC.t.sol)

[Vulnerability Report](./vulnerability-report.md)

## Installing Additional Dependencies

```
forge install GITHUB_OWNER_NAME/GITHUB_REPOSITORY_NAME
```

## Foundry Reference

### Mainnet forking

With anvil:

```bash
anvil --fork-url $RPC_URL/$API_KEY
```

Forge test on a network fork either normally or for a specific block:

```bash
forge test --fork-url $MAINNET_RPC_URL
```

```bash
forge test --fork-url $MAINNET_RPC_URL --fork-block-number 10000000
```

Forking with solidity scripting in one line:

```solidity
    function testCanCreateAndSelectInOneStep() public {
        // creates a new fork and also selects it
        uint256 mainnetFork = cheats.createSelectFork("mainnet");
    }
```

### Run PoC Test

```bash
forge test
```

### Run PoC Test with Full Call Trace

```bash
forge test -vvvvv
```

### Search for Function Selector

```bash
cast 4byte 0x70a08231
```

Prints:

```
balanceOf(address)
```

### Search for Event Signature

```bash
cast 4byte-event 0xddf252ad1be2c89b69c2b068fc378daa952ba7f163c4a11628f55a4df523b3ef
```

Prints:

```
Transfer(address,address,uint256)
```

### Generate Function Selector

```bash
cast sig "balanceOf(address)"
```

Prints:

```
0x70a08231
```

### Generate Event Signature

```bash
cast keccak "Transfer(address,address,uint256)"
```

Prints:

```
0xddf252ad1be2c89b69c2b068fc378daa952ba7f163c4a11628f55a4df523b3ef
```
