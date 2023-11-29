# soroban-examples <!-- omit in toc -->

Example contracts for Soroban using smartdeploy.


First need to install the binaries locally:

```bash
cargo install soroban-cli --version 20.0.0-rc4 --root target --debug
cargo install smartdeploy-cli --version 0.4.2 --root target --debug
```

create a new testnet account

```bash
./target/bin/soroban config identity generate test_smartdeploy --network testnet
```

Next change into a project:

e.g.

```bash
cd hello_world
cargo add smartdeploy-sdk
```

Add the following line to a `src/lib.rs`:

```rs
smartdeploy_sdk::core_riff!();
```

## Build:

```
make
```

## Publish
This calls smartdeploy's contract with the `call` subcommand to call the publish contract method. "contract_name" is the name of the published contract.

```bash
../target/bin/smartdeploy call smartdeploy --fee 10000 --source test_smartdeploy -- publish --contract_name hello_test1 --author test_smartdeploy --wasm-file-path ./target/wasm32-unknown-unknown/release/soroban_hello_world_contract.wasm
```

## Deploy

```bash
../target/bin/smartdeploy deploy --deployed-name hello_test_contract --published-name hello_test
```

Note, if your contract needs initialization you can add `-- --help`, to see the list of possible methods you can invoke when deploying.

## Call

```bash
../target/bin/smartdeploy call hell_test_contract -- hello --to world
```


## Possible contract errors:
```rust

#[contracterror]
#[derive(Copy, Clone, Debug, Eq, PartialEq, PartialOrd, Ord)]
#[repr(u32)]
pub enum Error {
    /// No such Contract has been published
    NoSuchContractPublished = 1,
    /// No such version of the contact has been published
    NoSuchVersion = 2,
    /// Contract already published
    AlreadyPublished = 3,

    /// No such contract deployed
    NoSuchContractDeployed = 4,

    /// Contract already deployed
    AlreadyDeployed = 5,

    /// Contract already claimed
    AlreadyClaimed = 6,

    /// Failed to initialize contract
    InitFailed = 7,
}
```






Follow along with [The Documentation](https://soroban.stellar.org/docs/).

Open a development environment on GitPod:

[![Open in Gitpod](https://gitpod.io/button/open-in-gitpod.svg)](https://gitpod.io/#https://github.com/stellar/soroban-examples)

WARNING: These implementations have not been tested or audited. They are likely
to have significant errors and security vulnerabilities. They should not be
relied on for any purpose.

Join us In the [Stellar Developers Discord server](https://discord.gg/stellardev)
