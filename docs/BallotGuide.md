## Decide Ballot Guide

In this guide we will explore all the different ballot interactions that can be performed on the Decide Governance Engine.

### Ballot Creation

To create a new ballot, a voter can call the `newballot()` action.

#### Ballot Statuses

Ballot statuses describe the current stage of a ballot's lifecycle. All new ballots begin with the `setup` status.

| Status | Description |
| --- | --- |
| setup | Ballot is being drafted. |
| voting | Ballot is currently open for voting. |
| closed | Ballot is closed and final results have been rendered. |
| cancelled | Ballot was cancelled, awaiting deletion. |
| archived | Ballot is currently archived and can't be deleted. |

### Voting Methods

Voting Methods describe how a ballot will react to voters with different token balances. One method splits a voter's balance among all of their selections, and another casts their full balance on each selection, for example.

| Voting Method | Description | Raw Weight | Transformed Weight Per |
| --- | --- | --- | -- |
| 1acct1vote | `Per Account Voting` Every voter gets 1 whole vote. Zero balances don't count. | 0.01 TEST | 1.00 TEST Each |
| 1tokennvote | `Total Direct Token-weighted Voting` Raw weight is applied to each option selected. | 3.00 TEST | 3.00 TEST Each |
| 1token1vote | `Proportional Direct Token-weighted Voting` Raw weight is split among all selections. | 3.00 TEST | 1.00 TEST Each |
| 1tsquare1v | `Proportional Quadratic Token-weighted Voting` Raw weight is split among selections and each weight squared. At ballot closure each option's total will be square-rooted | 3.00 TEST | 9.00 TEST Each |
| quadratic | `Total Quadratic Token-weighted Voting` Raw weight is square-rooted and split among selections. | 3.00 TEST | 9.00 Each |

#### Ballot Settings

Ballots have a range of settings that further alter their behavior.

| Setting | Description | Default |
| --- | --- | --- |
| lightballot | Marks as a light ballot. | false |
| revotable | Allows revoting on the ballot. | true |
| votestake | Reads voter's staked balance for casting votes. | true |
