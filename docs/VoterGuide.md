# Decide Voter Guide

In this guide we will explore all the different interactions available to voters on the Decide Governance Engine. 

## Getting Started

To get started as a Decide voter follow the steps below.

### Voter Registration

The first step to becoming a voter is voter registration. Successful registration will open a zero-balance account for the new voter, allowing them to obtain tokens and cast votes and interact with any future or existing ballot launched by the group.

1. **Find a Governance Group to Join**

Finding a Group to join is easy - just browse the group table and get the group symbol.

2. **Consider the Access Method**

Some groups are not open to the public and are instead only available based on an invite from a referrer. Typically the referrer must already be a voter for that group, but more tightly controlled `private` ballots require an invite from the group manager.

| Access Method | Description |
| --- | --- |
| Public | Open to everyone |
| Private | Requires referral by manager |
| Invite | Requires referral by voter |

3. **Call `regvoter()`**

Once a suitable group has been found, the voter (or the referrer) must call the `regvoter()` action on the Decide contract and supply the following arguments:

- Voter

    This is be the name of the new voter's blockchain account.

    EX: `testaccounta` or `account12345`

- Group Symbol

    This is the symbol of the group to join. Group symbols are expressed as the token's precision (i.e. the number of decimal places it has) followed by the ticker symbol of the group token.

    EX: `2,TEST` or `4,VOTE`

- Referrer (Optional)

    This is the account name of the refferer, if applicable. This account will authorize the registration of the `voter` account. If there is no referrer, then use `null`.

    EX: `account12345` or `null`

### Voting

After successful registration, the voter is allowed to begin casting votes on ballots.

1. **Obtain Tokens**

Once a voter is registered they must obtain tokens in order to cast a vote. The method for acquiring tokens will vary based on the group and project, but in general tokens can be acquired through a purchase, as a gift from another voter, or through the group manager directly.

2. **Find an Open Ballot**

After acquiring a balance of tokens, a voter can cast votes using the weight of those tokens. Any ballot with a status of `voting` is currently accepting votes.

3. **Cast Your Vote**

Once an open ballot has been found, all that's left to do is vote! Voters can submit their votes to the ballot by calling the `castvote()` action and supplying the following arguments:

- Voter

    This is the name of the voter's account.

    EX: `account12345`

- Ballot Name

    This is the name of the ballot to vote on.

    EX: `ballot1`

- Options

    This is the list of options that the voter wishes to vote on. The voter can vote for as many ballot options as they like, up to the max options limit set by the ballot.

    EX: `["option1", "option3", ...]`

### Unvoting

Sometimes voters want to retract previously submitted votes. Note that unvoting will rollback all votes cast on a ballot by a single user, but the vote receipt will remain on-chain until the ballot has reached its completion. This design allows the vote to track work performed on it and ensures that voters can't unvote and erase vote history.

### Staking and Unstaking

Certain groups will allow or disallow staking of tokens. If staking is allowed, vote weights will be pulled from the voter's staked amount instead of liquid when casting votes. 

## Voters Table Breakdown

Voters are the lifeblood of Decide, so it's important that voters remain knowledgable about how the platform works and how to interpret their own voter tables.

Table: `voters`

Scope: `your-voter-name`

| Field | Type | Description |
| --- | --- | --- |
| liquid | asset | Balance of liquid tokens. |
| staked | asset | Balance of staked tokens. |
| staked_time | time_point_sec | Time point the last stake or unstake occurred. |
| delegated | asset | Tokens delegated to a registered delegate. |
| delegated_to | name | The delegate account to which the voter's tokens are delegated. |
| delegation_time | time_point_sec | Time point the last delegation or undelegation occurred. |
