
![alt tag](https://github.com/gjamo/MarketsChain/blob/gjamo-patch-1/wf.current.architecture.png)

![alt tag](https://github.com/gjamo/MarketsChain/blob/gjamo-patch-1/wf.target.architecture.png)

![alt tag](https://github.com/gjamo/MarketsChain/blob/gjamo-patch-1/summary.roles.png)

![alt tag](https://github.com/gjamo/MarketsChain/blob/gjamo-patch-1/wf.user.contract.png)

![alt tag](https://github.com/gjamo/MarketsChain/blob/gjamo-patch-1/wf.bilateral.contract.png)
disintermediation
no need of CCP, collateral is held within blockchian
waterfall model in case of default can be managed automatically in blockchin

![alt tag](https://github.com/gjamo/MarketsChain/blob/gjamo-patch-1/wf.cleared.contract.png)

IPFS benefits: 3 layers:network & protocol, execution protocol independent/flexible, service provider,


# MarketsChain
Proof of concept on applying blockchain technology for front-to-back derivatives trading

## Issue in the current derivatives architecture
- Multiplicity of execution venues, affirmation platforms and systems within the banks (all of them because different market, different practices, multiple trade types have led to different practices, workflows and systems
- multiple workflows OTC cleared, bilateral and listed and adding regulation after regulation lead to this complexity
- third party interests and brokers
- all this complexity generate costs
- financial institutions doing a bit of everything, no clear responsbility between vendors, market makers, brokers, etc... is also participating in this lack of simplicity


## A credible alternative to the full suite of systems that financial institutions have implemented will need to fullfill (at least) this high level list of requirements
- Long term viability of financial services currently under regulatory pressure will come from the industrialisation and the commoditisation of services
- Roles performed by financial entities needs to be clearly broken down and streamlined
- ABility to quickly move of architecture / vendor
- Scalability
- Privacy: Transaction details (including counterparties) can not be freely accessible
  - want different level of privacy . authorisation for cpties  
  - Limited access to market participants / abillity to manage level of access
- Immediacy of trade capture
- Available globally 24h a day, 5 days a week
- Reliable services
- Counterparty traceability: KYC / AML
- Auditability of transactions and any amendments performed
- Interface with financial instituations internal systems & ledgers
- Flexible contract definition
- Support back-office functions (settlement, reconciliation,etc..)
- Ability to amend transaction
- Model to support ???
- Allow pre-execution / price discovery
- Collateral management
- Industry-wide blockchain initiative will require blockchain access controls
- Manage following models
  - trade executed externally (exchange, SEF or phone) before being recorded on the ledger
  - manage relationship
- Compliance: : validator accountability & registered users
- Finality of transaction
- security
- consensus protocol
  - power of participants needs to remain balance
  - high power usage of pow difficult to justify from marketing point of view
  - smaller users can not have hundreds of tb - end user should have to keep a copy of the full blockchain

- Note: We will consider execution / pre-exec / discovery / RFQ out of scope for now. For execution, although blockchain could be applicable to RFQ order, distributed technology such as IPFS will be more appropriate to central limit order book. Indeed CLOB requires high latency and data is not persistent and does not need to be stored in a ledger as such
- RFQ  fully discosed trading protocolo, buy and sell sides are known prior to execution
- Simplifying assumption: I would assume the only collateral and currency in the world is the blockchain currency. OBviously in reality some bridges between the two will need to be built, and should be described in further paper.

## Blockhain features required / solution
Objective of a distributed ledger to be used by a consortium of financial insitutions will be very different to an open blockchain protocol such as blockchain.  This is not about enabling a trustless contract mechanism but about being able to verify  identities / contract through cryptography
- Layer appproach / interchangeable technology so that banks are not stuck with particular vendor
- Blockchain 2.0 with smart contracts to manage blockchain access, market/static data, trade execution, trade capture/amendment, BO processing 
- Private chain in order to support the a consortium of financial institutions
- To achieve scalability, following features will be required
  - Blocks/transaction to be run in parallel: like ???
  - Not all nodes will have access: like ???
- Privacy through anonymisation ???
- POW will not be necessary and a set of block validators will be managed through a contract
  - registered validators (legally accountable)
  - proposer for each  block selected round robin from the set of validators
  - multiple rounds per block height possible
  - proposal signed 2 third validators
  - must not double vote
- mix of number private chains running in parallel
- wire protocol to incldue proposal, vote lockset
- blocks only created if there are transactions
- KYC / Aml: accounts to be registered to transact / suspicous transactions can be ttraced back to registrar
- registrars can block acccounts to transac with not recognised registrars
- blockchain protocol
  - gas mechanism: similar to Ethereum to avoid contract infinite loop, who will ditribute funds ?
  - states to be included in the block so that do not have to go through the full chain  .. see pros & cons of states???
- there should have some kind of weekly neeting / recap ... benefits???
- multiple chains to manage scalability: could be divided by transaction type or something else???
- decentralised data / market data contract


## Technology used for this SPOC
- Blockchain = Ethereum on a private network (planned to later upgrade to Hydrachain and implement multi chain linking within a node in Python)
- Contract = Ethereum EVM / Solidity
- Interface = Meteor / javascript
- All this will not allow full scalability nor privacy, so will have to wait development on ??? and ???

## Implementation roadmap for of the proof of concept
#### v0.1 15.03.2016: Implementation of a suite of Ethereum contracts and a meteor GUI for managing vanilla Interests Rates Swaps.
Meteor interface can be accessed on ????.meteor.com
You will need to launch a test ethereum client locally with the following command.

```
geth console ???
> ??? all contracts creation  and solidity files???
```

#### v0.2 coming soon: Upgrade to multi chain + remove the need of running an ethereum node

#### v0.x: focus on execution mechanism upgrade + more trade types, market data, more data to comply with regulation, etc...


# Detailed description

## Solidity contracts

#### Coin contract
- Name = Inter-Bank Coin
- Description = Currency for transaction within the consortium blockchain. Validators will start with a set amount of this currency and will flatten their balance at the end of day.
- Instance & Chain = One instance on "coin chain"

#### Block validator contract
- Name = Validator 
- Description = Mechanism to identify validators and update list of authorised validator
- Instance & Chain = One instance on "static data chain"

#### Customer contract
- Name = Customer
- Description = Mechanism for validators to on-board client (KYC,AML) while anonymising it to the rest of network
- Instance & Chain = One instance on "static data chain"

#### Market data contract
- Name = IB
- Description = Mechanism to reach consesus among validators on market data price (intra-day or at end of day)
- Instance & Chain = One instance per market data on "market data chain"

#### Bilateral IRS contract (existing and still prevaling mechanism in markets such as forex)
- Name = OTC-IRS
- Description = 
- Instance  & Chain = 

#### Billaterally Executed & Centrally Cleared IRS contract (expanded following Dodd-Frank and EMIR regulation)
- Name = cOTC-IRS
- Description = 
- Instance  & Chain = 

#### Exchange Traded & Centrally Cleared IRS contract
- Name = ETD-IRS
- Description = 
- Instance  & Chain = 

#### Blockchain IRS contract
- Name = BC-IRS
- Description = 
- Instance  & Chain = 

#### Bots to simulate market contract
- Name =
- Description = 
- Instance  & Chain = 


## Meteor interface

#### Features
- Create an account and get an automatc coin reward
- Participate to market data / price discovery
- Execute through the chain
- Capture trades through the chain
- Monitor live position
- Monitor automatic settlement
- Generate reporting
- Act as a validator and monitor client on-boarding and block validation???
- Act as a customer and book trades???

#### User guide
Detailed user guide is available on ???

#### Key assumptions & limitations

- This project is purely a proof of concept to validate the practicality of moving markets into the blockchain.  All coins distributed(entirely for free) and exchanged are run on a private / testing ethereum instance. Everything could be deleted without notice

END
