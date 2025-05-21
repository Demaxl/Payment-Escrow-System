# 🛠 Payment Escrow System

A smart contract-based escrow system for secure payments. Buyers deposit funds, and sellers can only withdraw them upon job approval or after dispute resolution. Built with Solidity and Foundry.

---

## 📦 Features

### 🔧 Core Features (MVP)

1. **Escrow Contract Creation**

    - A buyer can create a new escrow by specifying:
        - Seller address
        - Payment amount (ETH or ERC20)
        - Deadline / expected completion time

2. **Fund Deposit**

    - Buyer deposits funds into the escrow contract.
    - Contract holds funds securely (pull-over-push pattern).

3. **Mark Job as Completed**

    - Seller marks job as "completed"
    - Or buyer manually marks job as approved

4. **Release Payment**

    - Only the buyer can release funds once work is approved

5. **Refund Logic**

    - If the job is not completed in time, the buyer can request a refund

6. **Event Emissions**

    - Emit events like:
        - `EscrowCreated`
        - `JobCompleted`
        - `PaymentReleased`
        - `RefundIssued`

7. **Status State Machine**
    - Use an enum to manage contract state:
        - `Pending`, `Completed`, `Approved`, `Disputed`, `Refunded`, etc.

---

### 🚀 Advanced Features

8. **Time-based Dispute Window**

    - Add a delay before funds can be auto-released or refunded
    - E.g., 3-day window after seller marks as completed

9. **Dispute Mechanism**

    - Add an `admin` or DAO role to resolve disputes
    - Arbitrator decides who receives the funds

10. **ERC20 Support**

    - Allow stablecoin payments (e.g., USDC)
    - Use OpenZeppelin's `IERC20` interface

11. **Withdraw Pattern**

    - Use pull payments (seller calls `withdraw`) instead of push

12. **Modifiers & Access Control**
    - `onlyBuyer`, `onlySeller`, `onlyArbiter`
    - Optional: `Ownable` or `AccessControl` for roles

---

### 🎁 Bonus Features (Stretch Goals)

13. **Escrow Factory**

    -   Deploy multiple escrow contracts via a factory
    -   Track all escrows per user

14. **Reputation System**

    -   Sellers and buyers rate each other after completion
    -   Ratings stored on-chain or emitted via events

15. **Arbitrator DAO**

    -   Arbitrators stake tokens to resolve disputes
    -   Voting-based dispute resolution
    -   Earn a small fee for resolving disputes

16. **Frontend Integration**
    -   Build UI for:
        -   Create escrow
        -   Release funds
        -   Dispute/resolution flow
    -   Optional: Use [The Graph](https://thegraph.com/) for indexing

---

## 🔁 State Flow Diagram
