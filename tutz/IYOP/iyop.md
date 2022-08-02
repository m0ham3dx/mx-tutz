<h1 align="center"> IYOP - Immunefi Bug Bounty Replay for YOP Finance </h1>

----

<h1> TOC </h1>

1. [What ?](#what-)
2. [Repo](#repo)
3. [STEPS TO REPRODUCE](#steps-to-reproduce)
   1. [Step 1 - Clone Repository](#step-1---clone-repository)
      1. [Foundry Method](#foundry-method)
   2. [Step 2 - Configure `foundry.toml`](#step-2---configure-foundrytoml)
      1. [\[`foundry.toml`\] Used for the demo](#foundrytoml-used-for-the-demo)
   3. [Step 3 - Execute `forge test`](#step-3---execute-forge-test)
4. [DOWNLOAD TERMINAL DEMO](#download-terminal-demo)

----

# What ? 

1. This is the Bug Bounty Replay for [YOP Finance](https://medium.com/immunefi/how-to-use-foundry-to-poc-bug-leads-part-2-b7b3807400df)

2. This repo only discusses briefly procedures for making the demo. For a detailed understanding see the original writeup. 

3. [`forge`](https://book.getfoundry.sh/getting-started/first-steps) commands description are in their excellent manual. This repo will not get deep into its specifics, it is highly recommended to go through the manual before attempting this replay.

# Repo 

https://github.com/SergeKireev/foundry-poc-tutorial-II 

# STEPS TO REPRODUCE 

## Step 1 - Clone Repository 

Usually you would issue the following command 

```bash 
git clone https://github.com/SergeKireev/foundry-poc-tutorial-II
```
- But then you would have to deal with `git submodules`
- A better hack is using `forge install` , which will let you download all the referenced libraries locally

### Foundry Method 

```rust 
forge install --root ape/ --no-git --no-commit https://github.com/SergeKireev/foundry-poc-tutorial-II
```

Switches description

1. `-root` = Use this to redefine root path. All files will be downloaded under `/lib/` if you have missing file errors. Then consider remapping with [`forge remap`](https://book.getfoundry.sh/reference/forge/forge-remappings)

2. `--no-git` = This will remove all `git hub` related files, so you can upload to your own repo NOT as a submodule.
   
3. `--no-commit` = Removes any commits in the installation process

## Step 2 - Configure `foundry.toml`

1. You need an rpc 
   1. A public RPC was used for this from [HERE](https://chainlist.org/) - Note public rpc's are slow, which will be apparent in the demo
2. You need an [etherscan api](https://etherscan.io/apis)

### [`foundry.toml`] Used for the demo 

```toml
[default]
src = 'src'
out = 'out'
libs = ['lib']

eth_rpc_url = 'https://rpc.ankr.com/eth'
block_number = 14812830
etherscan_api_key = '5AZQMF9CXC8FCKIADX3NDTN1ETR3CI228U'
```

## Step 3 - Execute `forge test`

```rust 
forge test -vvvv --fork-url https://rpc.ankr.com/eth --fork-block-number 14811771
```

Switches Used 

1. `-vvvv` = verbosity level of traces 
   
2. `--fork-url` = for forking the chain 

3. `--fork-block-number` = specifiying the blocknumber

# DOWNLOAD TERMINAL DEMO 

[HERE](./files/IYOP%20by%20m0ham3dx.mp4) - `30MB`

