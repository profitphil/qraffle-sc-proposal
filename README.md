# Proposal to include Qraffle Smart Contract

## Proposal

Allow the **Qraffle Smart Contract** to be deployed on Qubic.

## Available Options

- **Option 0:** No, don't allow  
- **Option 1:** Yes, allow

---

## What is Qraffle?

**Qraffle** is a decentralized raffle and revenue-sharing system built on Qubic.

It provides:

- A **Standard Raffle** that runs automatically every epoch.
- **Token Raffles** that allow the community to propose and vote on raffles using different tokens.
- A built-in **DAO system** where registered participants earn a share of the protocol revenue and help govern the system.

Qraffle is designed to:

- Create ongoing utility and burn pressure for $QUBIC  
- Generate sustainable revenue for shareholders and DAO registrars  
- Provide a fun, transparent raffle experience every epoch

---

## Qraffle Solution

Qraffle introduces an **epoch-based raffle system** with a built-in DAO:

1. A **Standard Raffle** that runs automatically every epoch using $QUBIC.
2. **Token Raffles** that can be proposed, voted on, and executed by community registrars.
3. A **revenue-sharing model** where fees are split between burns, shareholders, registrars, protocol fees, and charity.
4. A **DAO system** where anyone meeting the staking requirements can register, vote, and earn a cut of the revenue.

In short:  
**Qraffle = On-chain raffle engine + DAO + revenue sharing + burn mechanics.**

---

## How It Works (Step by Step)

### 1. Standard Raffle (Every Epoch)

1. **Epoch Start → Raffle Opens**  
   - At the beginning of each epoch, the **Standard Raffle** is opened automatically.
   - Entry amount for this epoch is based on the **average entry size** submitted by registrars in the previous epoch.  
   - Initial entry amount is **1,000,000 QU**.

2. **Entries → Prize Pool Grows**  
   - Users submit entries in $QUBIC.
   - Prize pool is calculated as:  
     ```text
     Prize = number_of_entries * entry_amount * 0.8 (80%)
     ```
   - The remaining 20% goes to fees (see Fee Structure).

3. **Epoch End → Winner Selected**  
   - At the end of the epoch, the raffle closes.
   - **One winner** receives **80% of the total pool** in $QUBIC.

---

### 2. Token Raffle (By Proposal & Voting)

1. **Proposal Creation (by Registrars)**  
   Any registered DAO participant (“Registrar”) can submit a **Token Raffle** proposal with:

   - **Token name**
   - **Token issuer ID**
   - **Amount of an entry**

2. **Voting Period**  
   - The proposal is voted on by registrars during the epoch.
   - Voting **closes at the end of the epoch**.

3. **Raffle Activation**  
   - If the proposal passes, the **Token Raffle** is opened at the **beginning of the next epoch**.
   - The raffle opens at epoch start and closes at epoch end (same as Standard Raffle).

4. **Token Prize Distribution**  
   - Prize is calculated the same way:
     ```text
     Prize = number_of_entries * entry_amount * 0.8 (80%)
     ```
   - The winner receives **80% of the pool in the raffle token**.
   - Fees (the remaining 20%) are distributed using the same structure as Standard Raffle.

---

### 3. DAO System & Registrars

1. **Who Can Register?**  
   - Anyone can become a **Registrar** in the Qraffle DAO.
   - Registrars receive **5% of each raffle’s revenue** (shared among them).
   - Registrars are responsible for submitting **entry amount proposals** for the next epoch’s Standard Raffle.

2. **How to Register**

   To register in the system, a participant must:

   - Lock either:
     - **1,000,000,000 (1B) $QUBIC**, or  
     - **100,000,000 (100M) $QXMR**
   - Once registered, they:
     - Participate in governance (e.g., token raffle proposals, voting).
     - Share in the **5% Registrar revenue** whenever a raffle ends.

3. **Logout / Unregister**

   - A Registrar can choose to **log out** of the system.
   - There is a **5% logout fee** on their locked amount.
   - This logout fee is distributed to **Qraffle Shareholders** at the end of the epoch.

4. **Entry Amount Governance**

   - Each epoch, registrars submit their suggested **entry amount (in $QUBIC)** for the next epoch’s Standard Raffle.
   - The **average** of all submitted entry amounts becomes the **official entry amount** for the next epoch.

---

## Qraffle Key Features

| Feature                | Description |
|------------------------|------------|
| **Standard Raffle**    | Auto-opens every epoch using $QUBIC with 80% of the pool paid out to the winner. |
| **Token Raffles**      | DAO-driven raffles for arbitrary tokens (by proposal and vote), paying 80% of the token pool to the winner. |
| **Epoch-Based Logic**  | Raffles always align with epoch boundaries (open at epoch start, close at epoch end). |
| **DAO / Registrars**   | Anyone who meets the staking requirements can register, vote on parameters, and earn part of the fee revenue. |
| **Dynamic Entry Amount** | Standard Raffle entry amount is determined by the previous epoch’s average registrar-submitted amount. |
| **Revenue Sharing**    | Fee revenue is split between burn, shareholders, registrars, protocol fees, and charity. |
| **Charity Component**  | 1% of each raffle’s fee goes to a dedicated charity address (**@Kimz300**). |
| **Shareholders**       | Shareholders receive a 3% share from every raffle’s fee, plus logout fees from registrars. |

---

## Fee Structure

All raffles (Standard and Token Raffles) use the same fee structure:

- **Prize:** 80% of the total pool  
- **Total Fees:** 20% of the total pool

Breakdown of the **20% Fee**:

- **10%** → Burn (permanent $QUBIC burn)  
- **3%** → Shareholders  
- **5%** → Registrars (DAO participants)  
- **1%** → Protocol Fees  
- **1%** → Charity (**@Kimz300**)  

---

## Technical Implementation

From: [qubic/core#556](https://github.com/qubic/core/pull/566/commits/7384b6e27a7e87f13fa7cb30ff706a56c59a780a)

Please find the current implementation details below:
