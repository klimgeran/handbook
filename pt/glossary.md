---
title: "Glossary"
description: List of codenames, acronyms, lingo and crypto-specific words not everyone is familiar with.
category: education
lang: pt
ref: glossary
order: 100
version: 0
terms: # Keep them sorted!
  agora: "The codename for a decentralized, peer-to-peer marketplace built on Symbol to enable the trading of mosaics."
  ama: "Ask Me Anything. An open questions session."
  aml: "Anti-Money Laundering"
  andromeda: "The codename for a workflow product by NEM that enables users to visually architect and deploy dApps."
  apac: "Asia and Pacific region"
  apr: "Annual Percentage Rate."
  arbitrage: "When a trader purchases an asset in one place and sells it in another place to profit from a deviation in natural prices between markets."
  backrunning: "To broadcast <code>transactionA</code> with slightly lower gas (or fees) than an already pending <code>transactionB</code> so that <code>transactionA</code> gets mined <em>right after</em> <code>transactionB</code> in the same block."
  btc: "Bitcoin"
  cbdc: "Central Bank Digital Currency"
  cmc: "Coin Market Cap. A web page."
  csd: "Central Securities Deposit"
  dao: "Decentralized Autonomous Organization"
  ddh: "Decisional Diffie-Hellman"
  defi: "Decentralized Finance"
  dex: "Decentralized Exchange."
  dd : "Due Diligence"
  did: "Decentralized ID"
  dtc: "Direct To Consumer, i.e. mass market"
  e2e: "End-To-End"
  emea: "Europe, Middle-East and Africa"
  erc: "“Ethereum Request for Comment”. Commonly utilized to refer to a token standard on the EVM (such as ERC-20, ERC-721, ERC-1155)."
  eth: "Ethereum"
  evm: "Ethereum Virtual Machine"
  fft: "Fast Fourier Transform"
  flashbot: "?"
  frontrunning: "In context of cryptocurrencies: Trying to include <em>your</em> transaction <em>in front of</em> some other transaction. This is more important in case of DeFi markets, where gains can be made from front-running."
  fwiw: "For What It’s Worth."
  hermès: "Messenger of the Gods. Codename for Symbol’s next wallet project."
  ico: "Initial Coin Offering"
  ivc: "Incrementally Verifiable Computations"
  ip : "Intellectual Property"
  irs: "Internal Revenue Service. Who you pay your taxes to if you live in the US."
  kairos: "<em>From Ancient Greek: “The right, critical, or opportune moment.”</em><br>The codename for a collectible card game, built on top of Symbol. <a href=\"https://nem-software.atlassian.net/wiki/spaces/CD/overview?homepageId=633766243\">Kairos</a>."
  kyc: "Know Your Customer"
  latam: "Latin America (Central and South America)"
  m&a: "Mergers & Acquisitions (NOT a chocolate candy)"
  mev: "Miner-Extractable Value - process of reorganising transactions inside a block by miners, to gain <em>something</em> (might be covered by secret contract)"
  mosaic: "A representation of any kind of value on Symbol (both fungible and non-fungible)."
  nam: "North America"
  nem: "The new economy movement"
  ngl: "NEM Group Limited"
  nft: "A non-fungible token - a way to represent anything as an Ethereum-based asset."
  nsl: "NEM Software Limited"
  optimistic rollups: "An Ethereum layer 2 scaling solution. <a href=\"https://medium.com/stakefish/optimistic-rollups-how-they-work-and-why-they-matter-3f677a504fcf\">Optimistic Rollups</a>."
  perseus: "The codename for a end-to-end simulation platform by NEM that allows backtesting of network upgrades. Will launch with Symbol support but other blockchains can be added."
  sharding: "An Ethereum scaling solution. <a href=\"https://ethereum.org/en/eth2/shard-chains/\">Sharding</a>."
  poc: "Proof of Concept (NOT a consensus protocol)."
  poi: "Proof of Importance. The consensus protocol used by Symbol. Similar to PoS but measuring an account’s activity besides its stake."
  pos: "Proof of Stake. A consensus protocol."
  pow: "Proof of Work. A consensus protocol."
  rug pull: "A malicious maneuver where cryptocurrency developers abandon a project and run off with the funds."
  sandwitch: "A type of front-running technique that’s popular in DeFi. To make a sandwich, you find a pending transaction in the network and then try to surround the network by placing one order <em>just</em> before the transaction (front-running) and one order just after it (back-running)."
  sxdh: "Symmetric External Diffie-Hellman"
  tps: "Transactions Per Second"
  xem: "NEM’s NIS1 blockchain native currency"
  xym: "NEM’s Symbol blockchain native currency"
---

{% assign sorted_terms = page.terms %}

| Name | Definition |
| ---- | ---------- |
{% for term in sorted_terms %}| {{ term[0] | upcase }} | {{ term[1] }} |
{% endfor %}
