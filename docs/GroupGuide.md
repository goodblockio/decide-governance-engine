# Decide Group Guide

In this guide we will explore all the different Group interactions that can be performed on the Decide Voting Platform.

#### What is a Governance Group?

A Group is a place to keep track of data about a certain type of token. Information like the current supply of tokens, the max supply, the group settings, and the name of the current group manager are all tracked on the Governance Group. Note that tokens cannot exist on Decide without an accompanying Governance Group.

#### What is a Group Symbol?

All groups are identified by the symbol of the tokens they manage - also called a Group Symbol. 

Note that Group Symbols contain the precision amount of the token as well as the actual ticker name. So a `1.000 TEST` token would have a symbol of: `3,TEST`. The number 3 for the three decimal places of precision, followed by a comma with no space, then the ticker symbol in all caps. Whenever prompted to supply a group symbol, remember to give it in this format.

## Getting Started

Follow these steps to get started creating your own Decide Governance Group:

### 1. Governance Group Setup

Any user on the Decide Voting Platform may create a new token group, complete with all the features Decide provides. Before creating a group, the creator needs to know a few things first: 

- **Manager:** the account that will be the manager of the group. This account is allowed to do things like mint new tokens, change settings, or lock the group.

- **Max Supply:** the total number of tokens allowed to exist at one time. The group symbol will be extracted from this value (including the token precision).

- **Access:** the accessibility of the group. This can be set to public, private, or invite. `Public` means that an account can register as a voter at any time. `Private` means the group manager will have to approve every new voter before they can register. `Invite` means any voter can invite another voter, provided the inviter is a registered voter themselves.

### 2. Send `newtreasury()` Transaction

Once the new settings are decided, the group is ready for creation. Actually creating it involves sending a `newgroup()` action to the `trailservice` contract and giving it your arguments like so:

```
cleos push action trailservice newtreasury '["account12345", "500.00 EXMPL", "public"]' -p account12345
```

In the above command we are creating the public `EXMPL` group, managed by the `account12345` account, and with a max supply of 500.00 tokens.

Note that sending a `newtreasury()` transaction can be done through almost any Telos block explorer, and even some wallets like Anchor Wallet.

### 3. Managing A Group

After the group has been successfully created its ready to start holding ballots - but first we have to register voters and mint tokens, otherwise there won't be any voters with tokens who can participate on our ballots.

In order to mint tokens we have to have a voter to hold them, so lets go ahead and register ourselves. Registering new voters is done by sending a `regvoter()` transaction to the `trailservice` contract. Similar to preparing for sending the `newgroup()` transaction, we also need to know a few pieces of information first:

- **Voter:** the name of the account to register as a voter.

- **Group Symbol:** the symbol of the group to register for. This includes the token precision (the number of decimal places the token uses).

- **Referrer:** the account that is referring the new voter, if any. If no referrer, then give `null` as an argument.

Depending on the access method, a group may require extra signatures from certain voters to qualify. Since we made our group public we don't need to worry about referrals.

```
cleos push action trailservice regvoter '["account12345", "2,EXMPL", null]' -p account12345
```

#### Group Settings

| Setting | Description | Default |
| --- | --- | --- |
| transferable | Allows tokens to be transferred. | false |
| burnable | Allows tokens to be burned by the manager. | false |
| reclaimable | Allows tokens to be reclaimed by the manager. | false |
| stakeable | Allows tokens to be staked. | false |
| unstakeable | Allows tokens to be unstaked. | false |
| maxmutable | Allows max supply to be mutated. | false |

#### Group Access

| Access Method | Description |
| --- | --- |
| Public | Open to everyone |
| Private | Requires referral by manager |
| Invite | Requires referral by voter |

-----

## Group Table Breakdown

Groups manage a lot of data, so it's important for managers to understand how groups work and how to read group information so they can best serve their voters.

Table: `treasuries`

Scope: `trailservice`

| Field | Type | Description |
| --- | --- | --- |
| supply | asset | Current circulating supply of tokens. |
| max_supply | asset | Maximum circulating supply of tokens. |
| access | name | Access method for becoming a voter. |
| manager | name | Account that can edit and lock the group. |
| title | string | Group title. |
| description | string | Group description. |
| icon | string | IPFS cid or URI pointing to group icon. |
| voters | uint32 | Number of voters registered. |
| delegates | uint32_t | Number of delegates registered. |
| committees | uint32_t | Number of committees registered. |
| open_ballots | uint16 | Number of ballots open for voting. |
| locked | boolean | Locked if true, unlocked if false. |
| unlock_acct | name | Account that can unlock the group. |
| unlock_auth | name | Authority that can unlock the group. |
| settings | map(name, bool) | List of group-wide settings with on/off states. |
