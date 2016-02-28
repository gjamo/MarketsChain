# MarketsChain
Proof of concept on applying blockchain technology for front-to-back derivatives trading

## A credible alternative to the full suite of systems that financial institutions have implemented will need to fullfill (at least) this high level list of requirements
- Scalability
- Privacy: Transaction details (including counterparties) can not be freely accessible
- Immediacy of trade capture
- Available globally 24h a day, 5 days a week
- Reliable services
- Counterparty traceability: KYC / AML
- Auditability of transactions and any amendments performed
- Interface with financial instituations internal systems & ledgers
- Flexible contract definition
- Support back-office functions (settlement, reconciliation,etc..)
- Ability to amend transaction
- Model to support
- Allow pre-execution / price discovery
- Industry-wide blockchain initiative will require blockchain access controls

## Blockhain features & Technology to be used for the POC
- Blockchain 2.0 with smart contracts to manage blockchain access, market/static data, trade execution, trade capture/amendment, BO processing 
  => Ethereum / EVM capabilities
- Private chain in order to support the a consortium of financial institutions
  => Hydrachain
- To achieve scalability, following features will be required
  - Blocks/transaction to be run in parallel
  - Not all nodes will have access
  => on long term some research by ???? and ??? will enable this. For the POC we will create multiple chain with Hydrachain and implement the ability for nodes to connect to those multiple chains ???
- Privacy through anonymisation ???
  => ???
- POW will not be necessary and a set of block validators will be managed through a contract

## Implementation of the proof of concept
### v0.1 15.03.2016: Implementation of a suite of Ethereum contracts and a meteor GUI for managing vanilla Interests Rates Swaps.
Meteor interface can be accessed on ????.meteor.com
You will need to launch a test ethereum client locally with the following command.

```
geth console ???
> ??? all contracts creation  and solidity files???
```

### v0.2 coming soom: Upgrade to effective multi chain in testing + remove the need of running an ethereum node


