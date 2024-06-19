---
id: litentry-dashboards
title: Litentry Dashboards
sidebar_label: Litentry
description:
    Litentry is a decentralized AI blockchain that rewards knowledge creation and sharing. Its LIT token supports the AI economy by incentivizing contributions to the OriginTrail Decentralized Knowledge Graph (DKG). Litentry builds upon the groundwork established by its predecessor, the OriginTrail Parachain (OTP). This transformation into Litentry was facilitated through a community governance vote on OTP in December 2023.
keywords: [polkadot, dashboard, dune, litentry, DKG, OTP, knowledgeasset]
slug: ../litentry-dashboards
---

# Litentry Dashboards

## Overview

Litentry is a decentralized AI blockchain that rewards knowledge creation and sharing. Its LIT token supports the AI economy by incentivizing contributions to the OriginTrail Decentralized Knowledge Graph (DKG). Litentry builds upon the groundwork established by its predecessor, the OriginTrail Parachain (OTP). This transformation into Litentry was facilitated through a community governance vote on OTP in December 2023.

## Featured Dashboards on Dune

Here you'll find a variety of dashboards that help visualize data from the Moonbeam parachain:

- [Litentry](https://dune.com/substrate/litentry): A comprehensive analysis of Litentry, including: DKG, knowledge asset, asset, and XCM analysis.

## Key Tables

Data from the Litentry parachain is organized into several key tables: `litentry.balances`, `litentry.blocks`, `litentry.calls`, `litentry.events`, `litentry.extrinsics`, `litentry.transfers`.

## Useful Queries

Currently, there are no specific useful queries provided. Please check back later as this section
will be updated with materialized queries for Litentry.

## Getting Started with Queries

To get started with querying data from Unique, you are welcome to use the mentioned materialized
queries. You can use the following DuneSQL queries as examples:

```sql title="Litentry Knowledge Asset Distribution" showLineNumbers
SELECT DISTINCT
  get_href (
    'https://dkg.origintrail.io/profile?wallet=' || cast(To as VARCHAR),
    CONCAT(
      SUBSTR(To, 1, 4),
      '...',
      SUBSTR(To, LENGTH(To) - 3)
    )
  ) as Holder_URL,
  CONCAT(
    SUBSTR(To, 1, 4),
    '...',
    SUBSTR(To, LENGTH(To) - 3)
  ) as Holder,
  COUNT("Token ID") as "# of Tokens"
FROM
  query_3695045
GROUP BY
  To
ORDER BY
  "# of Tokens" DESC
```

Query result:

<iframe src="https://dune.com/embeds/3696553/6219067" height="350" width="100%"></iframe>

:::info DuneSQL Reference

For more information on DuneSQL, please refer to the [DuneSQL Cheatsheet](../dunesql-cheatsheet.md)
and
[DuneSQL Official Documentation](https://docs.dune.com/query-engine/Functions-and-operators/index).

:::

