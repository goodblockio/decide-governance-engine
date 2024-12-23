# Decide Governance Engine

Decide Governance Engine (DGE) is an on-chain governance engine designed and built by GoodBlock (@goodblockio) initially for use on the Telos Blockchain Network and other blockchains. DGE offers an extensive suite of voting services and DAC/DAO tools for both users and developers.

## Overview

DGE provides robust decentralized governance services to any blockchain where it is deployed. These include: 

* `Polls`
* `Elections`
* `Designation of Voting Committees`
* `Designation of Funding Authorization`
* `Bylaws Amendment`
* `Funding/Works Program Proposals`
* `Dispute Resolution`
* `Governance Group Creation and Committee Management`

Each of these is highly modular and configurable and can be extended beyond the blockchain system level to user-created groups.

Other unique advantages of DGE include:

* `Prevention of Double-voting Token-weighted Balances`
* `Automated Execution of Ballot Outcomes`
* `Proof of Voting`


## Features and Services

* `Secure Ballot Hosting`

    DGE allows users of any blockchain where it is deployed to create and publish a public ballot that is secured and hosted through Decide. During ballot creation, the ballot publisher selects a specific token to use for counting votes. As used on Telos, a token called `VOTE` is constantly rebalanced against TLOS system token balances of every account to ensure no tokens can be double-voted. The Decide Governance system offers additional services for creating privately managed tokens that ballots can use for counting votes instead.

* `Advanced Voting Methods`

    The Decide Governance Engine boasts an extensive set of voting methods that transform how votes are applied to ballot options. With these voting methods, ballot publishers are able to customize how they want to handle differences in voters' token balances and how those tokens should be cast among multiple choices on the ballot. Examples include `Per Account Voting` a.k.a `One Account, One Vote`, `Direct Token-weighted Voting` a.k.a. `One Token, One Vote`, and `Quadratic Token-weighted Voting`. These vote-counting methods can be extended to additional models such as `Ranked Choice Voting` and `Verified Identity Voting` a.k.a. `One Identity, One Vote`.

* `Custom Governance Groups`

    Any user on a blockchain that has deployed DGE (if so configured) can create a custom governance group that automatically inherits Decide's entire suite of voting services. These groups govern the minting and distribution of tokens and can also be customized to allow or disallow specific token behaviors like transferring, burning, staking, or reclaiming. Once a governance group has been created, any voter with a balance of its tokens may publish public ballots accessible to all other holders of that same token (within the permissions configured for the group).

* `Committee Management Tools`

    DGE offers a suite of committee creation and management actions that are available to any active token treasury and its voters. Developers can also hook their external smart contracts into Decide's committee tools to enable complete on-chain management of committees and their members.

* `Traceable Vote Integrity`

    DGE's custom rebalance system allows workers to recalculate vote weights when a voter's token balance changes. Workers who perform this service are eligible for payment rewards in proportion to the amount of work they have performed compared to all other workers in the treasury. Future updates will allow for optional identity services to further enhance voting and platform features.

* `Integrated Payroll System`

    All governance groups created on DGE have access to Decide's payroll system, allowing managers to continuously fund operations within their own treasury. Multiple payrolls can be created under a single governance group, each with their own bucket of funds that are released to designated recipients at a customizable rate.

* `Optional Light Ballots`

    Light ballots disable the on-chain vote tracking portion of the voting process - this allows for developers to track votes in an off-chain database that is built by an [Iris](https://github.com/CALEOS/iris-client), [Demux](https://github.com/EOSIO/demux-js), or Spectrum style service instead. 
    
    This option enables DGE to power vastly more voting services by saving system resource costs for both the platform and voters, while at the same time retaining the complete traceability and auditability benefits offered by the decentralized blockchain.

* `Profitable Worker Services`

    DGE incorporates a suite of janitorial actions that incentivize workers on the network to maintain an optimized voting system. Workers are paid proportionally for their work in keeping the platform clean and balanced for all users.

## Telos Decide Documentation

Full docuementation can be found in the [Decide Governance Engine Docs](https://docs.decidevoter.app/decide/introduction).

| Name | Description |
| --- | --- |
| [Starter Guide](docs/StarterGuide.md) | Breakdown of features for developers. |
| [Voter Guide](docs/VoterGuide.md) | How to become a voter and participate in ballots. |
| [Governance Group Guide](docs/GroupGuide.md) | How to create and manage Governance Groups. |
| [Worker Guide](docs/WorkerGuide.md) | How to perform work and the types of jobs available. |
| [Contract API](docs/ContractAPI.md) | Full Action and Table Breakdown. |

## Interfaces

### [Decide Voter mobile app](https://decidevoter.app)
A mobile app for iOS and Android created by GoodBlock. (Proprietary)

### Telos App
A web app for Telos Decide interaction by the Telos Core Developers. (Open Source)

### [EASE Protocol Super App](https://easeprotocol.com)
A mobile and web Super App interface for blockchains built on the EASE Protocol - under construction. (Open Source and Proprietary modules)

### WAX OIG App 
A web app interface for voting for the Office of the Inspector General of the WAX Blockchain

## Roadmap

### Ongoing

- Platform Optimization

### Q2 2025

- Integration into EASE Protocol Super App interface
- Decide Enterprise enhancements by GoodBlock (Proprietary and Open Source components)

### Q3 2025

- Additional Voting Methods: Ranked Choice Voting

### Q4 2025

- Identity Services via EASE Protocol Digital Identity
- Integration of secret ballot voting on EASE Protocol

## References

1. [Voting Methods by Eric Pacuit - Stanford Encyclopedia of Philosophy](https://plato.stanford.edu/entries/voting-methods/#CritForCompVotiMeth)

## Contributing to Decide Governance Engine

Decide Governance Engine is an open-source governance engine where contributions and improvements are welcomed by the community.

To make a contribution, simply fork this repo and submit a PR for your changes. In order to avoid duplication of work, it's best to engage with the community first to determine what would be an acceptable addition to the platform.


## Development History

The development history of this repository was truncated when the Telos Blockchain code repositories were migrated to a new group and examples of the earliest history of this repository were omitted and altered versions were substituted. Decide Governance Engine was originally a creation of Horn of the Moon LLC, dba "GoodBlock" a Washington State (USA) limited liability company. Project architect and leader: Douglas Horn, Lead developer: Peter Bue, Associate developer: Stephen Craig Branscom.
