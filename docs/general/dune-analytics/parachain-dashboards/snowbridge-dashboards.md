---

id: snowbridge-dashboards
title: Snowbridge Dashboards
sidebar_label: Snowbridge
description:
    Snowbridge is a general-purpose, trustless, and decentralized bridge that connects Polkadot and Ethereum. This bridge facilitates communication between any Polkadot parachain and Ethereum using Polkadot's XCMP messaging protocol. Parachains can send XCM instructions to BridgeHub, leveraging Snowbridge for cross-chain interactions.

    For more details on bridging with Kusama, please refer to our [BridgeHub Dashboard](https://dune.com/substrate/bridgehub).

keywords: [polkadot, ethereum, dashboard, dune, snowbridge]
slug: ../snowbridge-dashboards
---

# Snowbridge Dashboards

## Overview

Snowbridge is a general-purpose, trustless, and decentralized bridge that connects Polkadot and Ethereum. This bridge facilitates communication between any Polkadot parachain and Ethereum using Polkadot's XCMP messaging protocol. Parachains can send XCM instructions to BridgeHub, leveraging Snowbridge for cross-chain interactions.

For more details on bridging with Kusama, please refer to our [BridgeHub Dashboard](https://dune.com/substrate/bridgehub).

## Featured Dashboards on Dune

Here you'll find a variety of dashboards that help visualize data from the Snowbridge protocol:

- [Snowbridge](https://dune.com/substrate/snowbridge): A comprehensive analysis of Snowbridge, including: Ethereum Related On Chain Data Analysis, Analysis of Messages with Ethereum.

## Key Tables

Data from the Snowbridge protocol is organized into several key tables: `bridgehub.balances`, `bridgehub.blocks`, `bridgehub.calls`, `bridgehub.events`, `bridgehub.extrinsics`, `bridgehub.transfers`.

## Useful Queries

Some of the most important queries for Snowbridge are mentioned here.

| Subject Area                     | Query                                                       | Description                                  |
|----------------------------------|-------------------------------------------------------------|----------------------------------------------|
| Token Sent From Ethereum         | [query_3828274](https://dune.com/queries/3828274)           | Find tokens sent from the Ethereum chain     |
| ForeignAsset Mint & Burn On Assethub | [query_3828126](https://dune.com/queries/3828126)           | Find tokens minted and burned on Assethub    |

## Getting Started with Queries

To get started with querying data from Snowbridge, you are welcome to use the mentioned materialized
queries. You can use the following DuneSQL queries as examples:

```sql title="Polkadot BridgeHub Outbound Msg Sent To Ethereum" showLineNumbers
SELECT DISTINCT
  block_time,
  block_number,
  block_hash,
  extrinsic_id,
  extrinsic_hash,
  event_id,
  section,
  method,
  CAST(JSON_VALUE(data, 'strict $[0]') AS varchar) AS message_id,
  CAST(JSON_VALUE(data, 'strict $[1]') AS uint256) AS nonce
FROM
  bridgehub.events
WHERE
  section = 'ethereumOutboundQueue'
  AND method = 'MessageAccepted'
```

Query result:

<iframe src="https://dune.com/embeds/3831797/6444701" height="350" width="100%"></iframe>

:::info DuneSQL Reference

For more information on DuneSQL, please refer to the [DuneSQL Cheatsheet](../dunesql-cheatsheet.md)
and
[DuneSQL Official Documentation](https://docs.dune.com/query-engine/Functions-and-operators/index).

:::
