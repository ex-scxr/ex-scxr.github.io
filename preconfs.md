---
layout: article
title: Preconfirmations for the Average Joe
permalink: /research/preconfs/
---
<div class="blurred-title-container">
    <img src="{{ 'assets/images/preconfs/Ggc_B4Ha8AAySzQ.jpg' | relative_url }}" alt="Article Image" class="blurred-background">
    <h1 class="blurred-title">{{ page.title }}</h1>
</div>
#### Written by:**[Cecilia Zhang](https://x.com/ceciliaz030)**
#### January 4th, 2025

2025 is bound to be a year of consumer-facing experience. Meanwhile, infrastructure should center around apps as we see examples like Unichain and Hyperliquid. It's reaffirmed that being fast and cheap remains the No. 1 principle of UX.

We want to deliver the best UX through the base layer while preserving decentralization and neutrality to the greatest extent. Throughout 2024, the developer community has focused on preconfirmation—a feature that achieves this purpose once the base layer ecosystem matures.

In this series, we'll explain what Preconfirmation means for Ethereum users, validators, and applications (Based Rollups included), and explore what needs to happen to maximize its UX benefits.

## To The User
Without technical jargon, this is what may happen:
1. You may use a preconf-enabled wallet that integrates at least one preconf gateway.
2. Your transaction will be confirmed almost instantly, but you will pay a tip.
3. Your tip goes to the gateways, validator, and perhaps builder depending on how they structure the payment.
4. The gateway provides insurance of transaction settlement on-chain over some specified time.
5. In a future slot, the gateway finds the validator to include your transaction (by enforcing builders).
6. If your transactions end up not included, some validator will get slashed.

![]({{'assets/images/preconfs/GgczPnAa4AAclnF.jpg' | relative_url}}) Preconfirmations give an extra time variable in how transactions are priced. You can still pay the standard base fee + tip if you don't mind waiting for L1 blocktime, or you can tip extra for delivery insurance and fast confirmation. Note that this is only an insurance. It does not mean that your transaction is already on-chain. Insurance is backed by economic security, meaning the insurers, in our case the gateway and validators (or whatever protocol sitting in between), put down substantial collaterals to pledge for the results. This also means the users of preconfirmation are taking the cascading risks.

## How much will you pay?
Currently, only Inclusion Preconf exists, which means the gateway can only guarantee the inclusion of transactions. A more advanced type called Execution Preconf could have greater significance, especially for certain applications. With Execution Preconf, if you're swapping tokens, you are promised the pool's outcome, including price and amount with slippage—not just confirmation that your swap was included (which could still fail). This sophisticated version is more difficult to price and will cost more.

For simplicity, we only discuss the pricing of Inclusion Preconf. <a href="https://research.lido.fi/t/a-pricing-model-for-inclusion-preconfirmations/9136" target="_blank">This article</a> presents a model of the validator’s expected return under a given amount of JIT-auctioned gas and preconfirmed gas. Long story short, the model predicts that an ETH transfer (21,000 gas) costs:

* **0.61 GWEI** when the existing preconfirmation = **0**
* **1.17 GWEI** when the existing preconfirmation = **15M gas**
* **15 GWEI** when the existing preconfirmation = **30M gas**

![]({{'assets/images/preconfs/Ggc0qDFasAATCDW.jpg' | relative_url}})

## What else on UX?
A huge bull case on the front end is new wallet features. Let’s think big and speak with very utopian terms - a wallet may offer users $5.99/mo for instant confirmation of all transactions, and an upgraded plan of $9.99/mo for swapping with superior slippage control. Furthermore, with Account Abstraction, you can spend all your tokens without an extra step of approval, and perhaps get your gas fees sponsored for $15.99/mo.

Do these sound like good deals? Several mechanisms need to work together behind the scenes to make this possible. In <a href="https://docs.luban.wtf/learn/fundamentals/preconf_fungibility" target="_blank">Luban’s fungible preconf mode</a> wallets will purchase blockspace in bulk from gateways for future settlement. However, a caveat is contentious activities should be avoided when using this service. If you try to ape memecoins using preconfirmation, your transaction might fail when it reaches L1 because the coin would have been sold out.

![]({{'assets/images/preconfs/Ggc1xkCa8AIH6HL.jpg' | relative_url}}) There are some potential implementations for improving slippage. With execution preconfirmation, it’s possible for service providers to insure you against a range of slippage <a href="https://ethresear.ch/t/based-proposer-commitments-ethereum-s-marketplace-for-proposer-commitments/19517" target="_blank">validators will commit to the insured states</a>, and then searchers or builders can fulfill the criteria. Without execution preconfirmation, the wallet can integrate DEX with <a href="https://sorellalabs.xyz/writing/a-new-era-of-defi-with-ass" target="_blank">Application-Specific Sequencing (ASS)</a> and connect to the app-specific mempool. This allows your transaction to be included as part of the ASS bundle by inclusion preconfirmation.

What about gas sponsorship and the batching of UserOps? This scenario is <a href="https://research.chainbound.io/integrating-account-abstraction-and-inclusion-preconfirmations" target="_blank">introduced by Chainbound.</a> At a high level, Account Abstraction allows another entity to send transactions on your behalf with prior authorization, and this entity can also pay for gas. Service providers aiming to attract customers with gas sponsorship can batch these authorized transactions to reduce costs. Preconfirmation naturally complements this system, because AA wallets can do the following:

1. **Batch as much as possible to amortize user cost;**
2. **Settle in the future instead of every slot to lower fixed costs;**
3. **Provide instant preconfimation to users.**

⠀This is an enabler of the economics of scale and a definitive upgrade on Ethereum UX.

## Summary
Preconfirmation is nothing fancy, it's akin to a bridge directly from users to Ethereum validators. As this ecosystem matures, wallets would sit on proposer commitments to serve what you need, rather than selling bundles that potentially rip you off. Best of all, features previously exclusive to centralized exchanges and custodial wallets will become available in a non-custodial setting, powered by the base layer.

In the upcoming section, we will discuss how Preconfirmation will benefit the validators.