# Decide Starter Guide

In this Starter Guide, we will explore Decide's suite of platform services available to any prospective contract developer. We will follow an example throughout the guide to help establish the general flow and lifecycle of running a ballot, group, and/or committee. The Decide Contract API will be introduced in this guide as certain sections become relevant to the task at hand. 

For a more straightforward breakdown of Decide's Contract API without the example fluff, see the [Decide Contract API](ContractAPI.md) document.

## Understanding Decide's Role

Decide's primary purpose is to consolidate all the common boilerplate functions of voting contracts into a single chain-wide service available to organizations, developers, and general users.

For developers, this means they can leave the user registration, token management, and vote tracking up to Decide, and instead design their contracts to interact with Decide for drafting, launching, and reacting to ballot results. This way, external Smart Contracts can *contractually* interpret and act on these results according to their intended use cases.

For organizations, this means they can confidently track crucial ownership and participation in dBusiness activities, and Decide's robust toolset offers fine granularity of control over token distribution and behavior allowing businesses to adjust for their personal regulatory needs.

### Decide Voting Platform Services

| Service | Description | Cost |
| --- | --- | --- |
| Voting | Voter registration, token balances, voting, unvoting, staking, and unstaking. | Free |
| Ballots | Ballot hosting, customization, and results broadcasting. | 30 SYS per ballot |
| Groups  | Group creation, locking/unlocking, verbose settings, worker fund, token minting, transferring, reclaiming, and burning. | 1000 SYS per group |
| Committees | Committee creation, management, security, and seat control. | 100 SYS per committee |
| Archival | Archive important ballots to preserve results. | 3 SYS per day |
| Workers | Participation, progress tracking, and profit incentives. | Free |

Note that the above fees are customizable through a BP multisig and might be adjusted by the Block Producers or by a Referendum from the Telos Community.

More information about each service can be found in the relevent documentation.

-----

## Building an External Contract

For this Starter Guide we will also walk through building a simple external contract to act on ballot results after ballot closure. Developers can use this example as a starting point for designing their own contracts.

In our contract, we will launch a new election ballot and then *contractually act* on the results broadcast by Decide's `broadcast()` action. Upon hearing the broadcast, our contract will read the final results, determine the winning candidate, and then send an inline action back to Decide to update our committee with the election winner.

> Guide: [Example Contract Integration](docs/ExampleGuide.md)

> Source:
[example.hpp](../contracts/example/include/example.hpp) / 
[example.cpp](../contracts/example/src/example.cpp)
