# Composability Article

# From Faster to Smoother

Ethereum’s [rollup-centric roadmap](https://ethereum-magicians.org/t/a-rollup-centric-ethereum-roadmap/4698) was designed to make Ethereum a better home for rollups to facilitate faster and cheaper transactions, and this approach has proven highly effective. Rollups now handle millions of Ethereum transactions at a fraction of the cost of L1. However, this success has introduced a new challenge: **fragmentation**.

Currently, rollups operate in silos, each with its own liquidity and state. This means users are stuck navigating bridges to move funds between chains, and developers must design complex multi-chain solutions, increasing overhead and attack surface area.

The focus is shifting from merely making Ethereum faster and cheaper to enhancing the user and developer experience. Enter **composability** and **interoperability**—the keys to unifying Ethereum’s isolated ecosystems.

---

## Some definitions

- **Interoperability**: The ability for rollups to communicate with each other. This involves transferring assets and data between chains, such as bridging tokens from one L2 to another.
- **Composability**: The ability for rollups to share both liquidity and state, enabling seamless interactions across chains. For example, taking a loan out on one rollup and using it as collateral for a trade on another—all within a single transaction.
- **Atomicity**: The "all-or-nothing" principle—operations are bundled together and succeed or fail entirely, ensuring there are no partial outcomes.

While interoperability connects rollups, composability ensures they function together as one cohesive system, creating a unified experience for users and developers.

---

## How Rollups Communicate 💬

### Intent-Based Interoperability 🕸️

- **What it is:** A basic form of communication between chains, where users express intents (“swap tokens on another chain”), and relayers or "fulfillers" complete these requests. It provides foundational connectivity between chains, but makes no guarantees beyond the execution of a single intent.
- **How it works:** Communication happens through relayers that act on user instructions, typically leveraging bridge-based systems to move assets or data between chains. There is no shared state between chains, and each interaction is isolated and independent, relying on external operators to fulfill the requests.
- **Guarantees:**
    - **Atomicity:** ✅ – Each intent succeeds or fails on its own.
    - **Synchronicity:** ❌ – No real-time interactions; each action is processed in isolation.

---

### Asynchronous Composability - Message Passing 📬

- **What it is:** A method where rollups communicate by passing messages that are processed independently without requiring immediate synchronization.
- **How it works:** Rollups emit event logs consumed by other chains. These logs relay information, allowing operations to proceed independently on each chain without strict timing constraints.
- **Guarantees:**
    - **Atomicity:** ❌ – A failure on one chain doesn’t affect others.
    - **Synchronicity:** ❌ – Delays in message propagation can result in lagged updates.

---

### Synchronous Composability - (Based) Shared Sequencing 🏗️

- **What it is:** A high level of integration between chains enabling rollups to operate cohesively, creating the experience of a single, unified chain for end users. Transactions are treated as a single unit, ensuring consistency and seamless interaction across chains.
- **How it works:** Transactions are bundled into a unified process using shared sequencing, where a central sequencer coordinates the ordering of transactions across rollups. This ensures that all involved chains update their states all at the same time, providing a seamless and atomic user experience. Unlike message passing, which relies on asynchronous communication and can introduce delays or inconsistencies, shared sequencing guarantees that cross-chain operations are treated as a single cohesive action. If any part of the transaction fails, the entire operation reverts, maintaining consistent states across chains.
- **Guarantees:**
    - **Atomicity:** ✅ – All operations succeed or fail as a single unit.
    - **Synchronicity:** ✅ – Real-time updates across all rollups.

---

## To Wrap Things Up

The evolution of composability has delivered solutions that address fragmentation by tailoring guarantees of atomicity, synchronicity, and scalability to specific needs. Ethereum’s ecosystem now supports diverse interactions, from simple intent-based interoperability to fully synchronous composability, creating a cohesive network that enhances both usability and scalability for users and developers.