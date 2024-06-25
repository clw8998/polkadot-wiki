---

id: hyperbridge-dashboards
title: Hyperbridge Dashboards
sidebar_label: Hyperbridge
description:
    Hyperbridge is a protocol designed for secure blockchain interoperability. It offers consensus and state proof verification by verifying various proofs off-chain and reporting securely on-chain, enhancing scalability and security. The protocol also utilizes cryptographic proofs to create a decentralized relayer network, enabling permissionless cross-chain communication. Additionally, Hyperbridge aggregates multiple proofs to create a single proof for cross-chain messages, improving efficiency and reliability. 

    For more information, visit [Hyperbridge Doc](https://docs.hyperbridge.network/).

keywords: [polkadot, hyperbridge, dashboard, dune, XCM]
slug: ../hyperbridge-dashboards
---

# Hyperbridge Dashboards

## Overview

Hyperbridge is a protocol designed for secure blockchain interoperability. It offers consensus and state proof verification by verifying various proofs off-chain and reporting securely on-chain, enhancing scalability and security. The protocol also utilizes cryptographic proofs to create a decentralized relayer network, enabling permissionless cross-chain communication. Additionally, Hyperbridge aggregates multiple proofs to create a single proof for cross-chain messages, improving efficiency and reliability. 

For more information, visit [Hyperbridge Doc](https://docs.hyperbridge.network/).

## Featured Dashboards on Dune

Here you'll find a variety of dashboards that help visualize data from the Hyperbridge parachain:

- [Hyperbridge](https://dune.com/substrate/hyperbridge): A comprehensive basic metrics analysis of Hyperbridge, including: Daily Transfer Quantity and Total Amounts, Daily Extrinsics, Events Number, Daily Fee Used.

## Key Tables

Data from the Snowbridge protocol is organized into several key tables: `hyperbridge.balances`, `hyperbridge.blocks`, `hyperbridge.calls`, `hyperbridge.events`, `hyperbridge.extrinsics`, `hyperbridge.transfers`.

## Useful Queries

Since Hyperbridge was just approved through the Polkadot crowdloan in April 2024, there is currently not enough on-chain data for us to proceed with the next step of analysis.

We will update the dashboard content once sufficient data is available.

## Getting Started with Queries

To get started with querying data from Hyperbridge, you are welcome to use the mentioned materialized
queries. You can use the following DuneSQL queries as examples:

```sql title="Hyperbridge Daily Average Block Time" showLineNumbers
WITH avg_block_time AS (
    SELECT
        DATE(logDT) AS logDT,
        avg_time_diff
    FROMHyperbridge Daily Average Block Time
        "query_3587497(chain = '3367')" -- Daily Average Block Time
),
daily_block_cnt AS (
    SELECT
        DATE(block_time) AS logDT,
        COUNT(DISTINCT number) AS cnt
    FROM
        hyperbridge.blocks
    WHERE
        DATE(block_time) < CURRENT_DATE
    GROUP BY
        DATE(block_time)
    ORDER BY
        logDT
)
SELECT
    d.logDT,
    d.cnt,
    a.avg_time_diff
FROM
    daily_block_cnt d
LEFT JOIN
    avg_block_time a
ON
    d.logDT = a.logDT
ORDER BY
    d.logDT DESC

```

Query result:

<iframe src="https://dune.com/embeds/3859235/6491113" height="350" width="100%"></iframe>

:::info DuneSQL Reference

For more information on DuneSQL, please refer to the [DuneSQL Cheatsheet](../dunesql-cheatsheet.md)
and
[DuneSQL Official Documentation](https://docs.dune.com/query-engine/Functions-and-operators/index).

:::

