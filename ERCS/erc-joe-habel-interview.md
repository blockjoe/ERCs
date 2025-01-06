---
eip: XXXX
title: Introduce an Additional Impacts Section to ERCs and Interface EIPs
description: Add additional impact section to ERCs and Interface EIPs to aid in application layer standardization.
author: Joe Habel (@blockjoe)
discussions-to: N/A
status: draft
type: Meta
created: 2024-01-05
requires: 7329
---

## Abstract

Describes the motivation and rational for introducing additional an impacts
section in both ERC and Interface EIPs to help better identify the proper
audiences needed to better catalyze application developers around the process.

## Motivation

[EIP-7329](./eip-7329.md) split the ERCs and Interface EIPs from the main EIPs
repository to address the fact that discussions concerning concerning core
ethereum development and discussions concerning application development were
serving two divergent communities.

These changes created the separation between these communities to better
allow for discussions relevant to core developers to happen in one space,
and for discussions concerning application developers to happen in another.

With this space created, there is now room to look deeper into the needs
of the application developer community, and begin identify where further
"categorization" is needed to address the needs of the application layer.

Before further categorizations or process considerations should be made
about how to further refine the needs of the application layer, we should
first have a clear understanding of the dependencies that the application
layer has on both itself, and to core development.

While this impacts section will provide more clarity to help better
define the key groups affected by different kinds of application layer
standards proposals, even if no further process actions are taken, they
will at minimum provide a rough dependency graph for the existing application
layer, its developers, and core development.

## Specification

For ERC and Interface EIPs, an optional "Impact" section will be available.
This section will appear immediately following the current "Backwards
Compatibility" section. This section will have 3 new subsections:

1. "Upstream Impacts"
2. "Downstream Impacts"
3. "Replaces"

The "Upstream Impacts" subsection will cover any changes required from core
development teams. These are expected to be changes that need to be implemented
by core development teams, but aren't changes that involve network coordination
to implement. Some examples here might include needing Execution Layer client
teams to implement changes to an RPC method, or introducing an additional
prometheus gauge.

The "Downstream Impacts" subsection will cover any changes required from other
application layer teams. Using the same case of changing an RPC method, it
would be expected that web3 integration library developers and commercial
service providers are mentioned. Additionally, a proposal to migrate ERC-20 to
a new ERC standard would be expected to mention explorers, wallets, and
indexers as impacted parties.

Finally, the "Replaces" subsection will cover any intention to replace an
existing standard. This standard may or may not be already referenced as
an existing ERC or Interface EIP, but if it is not, the nearest point in
the existing relevant specification should be referenced instead.

## Rationale

While, [EIP-7329](./eip-7329.md) identified that there were too many divergent communities
within the EIPs repository, its specification created a "Core Development" and
"Everything Else" split. What is the "Application Layer" though is not a single
minded community. To give a framing to better continue discussing these personas,
let's look at 3 kinds of development:

1. Those **Building** Ethereum
2. Those **Building For** Ethereum
3. Those **Building On** Ethereum

The EIPs repository and the existing EIP process is best suited for the first
category, those **building** Ethereum, the core development.

What exists inside of both the ERC and Interface EIPs repositories are both
the second and third, those both **building for** and **building on**.

This distinction is important, because it highlights the difference between a
public goods developer in the application layer, and a commercial developer in
the application layer. Both of these groups are essential, but they have
divergent motivations, expectations, timeframe requirements, and dependencies.

Those who are building public goods, or broad integration tools **for**
Ethereum are far more likely to be already tuned into the core development
cycle, are possibly doing work that spans the gap between the core
development and application layers, and are more likely to be able to work
on a timeline that is accommodating of the core development teams.

Those who are building commercial software, are more likely to only be aware of
part of Ethereum development that matters to them, are likely doing work that
is focused directly on other application developers, and have less flexible
timing requirements.

By introducing the Upstream and Downstream Impact subsections, we can get a better
view into these dynamics within the application layer, and continue to further
refine the ERC and Interface processes to better accommodate these two key
application layer communities.

Related to both communities is the Replaces subsection. As it currently stands,
there is no versioning across standards. The goal of introducing the Replaces
section is to simply capture whether or not the application layer has a desire
for dynamically evolving standards, or if there is a desire to continue to
operate how things currently are.


### Objection: We already have a "requires" field in the header

While this is is true, this section only captures the dependencies
between existing EIPs/ERCs. This section likely covers a majority
of what would already be covered in the "Upstream Impacts" subsection,
but it misses capturing any requirements not defined in an existing
EIP/ERC.


### Objection: The data from the Impact section is too broad to justify this change

While the data provided in the Impact section won't allow for an immediate an
accurate application layer dependency map initially, introducing this section
broadly instead of in a categorization that would work as a header field allows
for finding the right granularity for more specifics.

In a future where better defined categories exist, the Impacts section still
remains useful for capturing better clarity for other parties about how exactly
this might impact them.

### Objection: This should be an  [EIP-1](./eip-1.md) proposal

I'll admit I'm blindly following [EIP-7329](./eip-7329.md) here.

> As the old programming adage goes: "Refactor first before adding any new
features."  Adding new processes specific to the post-split governing docs would
only confuse the existing process, adding special cases for one class of EIPs
that don't apply to another. It is precisely this kind of problem the proposed
split is aiming to change.

The proposed changes to the template section of ERC / Interfaces Standards
absolutely needs to be communicated in there first.

I largely kept this as a Meta-ERC for the sake of capturing the style flow of
the core template, but if the above structure would have made more sense as an
[EIP-1](./eip-1.md) proposal, then of course it lives there. Although, I think
figuring out what's the best way to preserve 7329's motivations for driving a
deeper split between EIP and ERC should be preferred here.

## Backwards Compatibility

### Existing Proposals

Introducing a new section to the template instead of a new header makes these
changes compatible with the existing ERC and Interfaces repositories as they
don't break any headers. Any changes to these processes would include adding
the check for the Impacts section in the automated CI reviewer process.

Existing proposals should be made available to be updated to optionally include
this new section at the authors' discretion, although this should not be a firm
requirement. Additionally, it can be considered that a reviewer is able to
offer proposed suggestions to existing proposals for the authors' approval, but
this approach requires a lot of load on a potential reviewer(s) set, and while
welcomed, isn't entirely needed.


## Security Considerations

This proposal only addresses the EIP and ERC proposal process and is not
expected to expose any new attack surfaces by virtue of its adoption.

## Copyright

Copyright and related rights waived via [CC0](../LICENSE.md).
