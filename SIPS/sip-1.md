---
sip: 1
title: SIP Purpose and Guidelines
status: Active
type: Meta
author: Superstring Community
        https://github.com/susytech/SIPs/blob/master/SIPS/sip-1.md
created: 2015-10-27
updated: 2015-12-07, 2016-02-01, 2018-03-21, 2018-05-29, 2018-10-17
---

## What is an SIP?

SIP stands for Susy Improvement Proposal. An SIP is a design document providing information to the Susy community, or describing a new feature for Susy or its processes or environment. The SIP should provide a concise technical specification of the feature and a rationale for the feature. The SIP author is responsible for building consensus within the community and documenting dissenting opinions.

## SIP Rationale

We intend SIPs to be the primary mechanisms for proposing new features, for collecting community technical input on an issue, and for documenting the design decisions that have gone into Susy. Because the SIPs are maintained as text files in a versioned repository, their revision history is the historical record of the feature proposal.

For Susy implementers, SIPs are a convenient way to track the progress of their implementation. Ideally each implementation maintainer would list the SIPs that they have implemented. This will give end users a convenient way to know the current status of a given implementation or library.

## SIP Types

There are three types of SIP:

- A **Standard Track SIP** describes any change that affects most or all Susy implementations, such as a change to the the network protocol, a change in block or transaction validity rules, proposed application standards/conventions, or any change or addition that affects the interoperability of applications using Susy. Furthermore Standard SIPs can be broken down into the following categories. Standards Track SIPs consist of three parts, a design document, implementation, and finally if warranted an update to the [formal specification].
  - **Core** - improvements requiring a consensus fork (e.g. [SIP5], [SIP101]), as well as changes that are not necessarily consensus critical but may be relevant to [“core dev” discussions](https://github.com/susytech/pm) (for example, [SIP90], and the miner/node strategy changes 2, 3, and 4 of [SIP86]).
  - **Networking** - includes improvements around [devp2p] ([SIP8]) and [Light Susy Subprotocol], as well as proposed improvements to network protocol specifications of [whisper] and [swarm].
  - **Interface** - includes improvements around client [API/RPC] specifications and standards, and also certain language-level standards like method names ([SIP6]) and [contract ABIs]. The label “interface” aligns with the [interfaces repo] and discussion should primarily occur in that repository before an SIP is submitted to the SIPs repository.
  - **SRC** - application-level standards and conventions, including contract standards such as token standards ([SRC20]), name registries ([SRC26], [SRC137]), URI schemes ([SRC67]), library/package formats ([SIP82]), and wallet formats ([SIP75], [SIP85]).
- An **Informational SIP** describes an Susy design issue, or provides general guidelines or information to the Susy community, but does not propose a new feature. Informational SIPs do not necessarily represent Susy community consensus or a recommendation, so users and implementers are free to ignore Informational SIPs or follow their advice.
- A **Meta SIP** describes a process surrounding Susy or proposes a change to (or an event in) a process. Process SIPs are like Standards Track SIPs but apply to areas other than the Susy protocol itself. They may propose an implementation, but not to Susy's codebase; they often require community consensus; unlike Informational SIPs, they are more than recommendations, and users are typically not free to ignore them. Examples include procedures, guidelines, changes to the decision-making process, and changes to the tools or environment used in Susy development. Any meta-SIP is also considered a Process SIP.

It is highly recommended that a single SIP contain a single key proposal or new idea. The more focused the SIP, the more successful it tends to be. A change to one client doesn't require an SIP; a change that affects multiple clients, or defines a standard for multiple apps to use, does.

An SIP must meet certain minimum criteria. It must be a clear and complete description of the proposed enhancement. The enhancement must represent a net improvement. The proposed implementation, if applicable, must be solid and must not complicate the protocol unduly.

## SIP Work Flow

Parties involved in the process are you, the champion or *SIP author*, the [*SIP editors*](#sip-editors), and the [*Susy Core Developers*](https://github.com/susytech/pm).

:warning: Before you begin, vet your idea, this will save you time. Ask the Susy community first if an idea is original to avoid wasting time on something that will be be rejected based on prior research (searching the Internet does not always do the trick). It also helps to make sure the idea is applicable to the entire community and not just the author. Just because an idea sounds good to the author does not mean it will work for most people in most areas where Susy is used. Examples of appropriate public forums to gauge interest around your SIP include [the Susy subreddit], [the Issues section of this repository], and [one of the Susy Gitter chat rooms]. In particular, [the Issues section of this repository] is an excellent place to discuss your proposal with the community and start creating more formalized language around your SIP.

Your role as the champion is to write the SIP using the style and format described below, shepherd the discussions in the appropriate forums, and build community consensus around the idea. Following is the process that a successful SIP will move along:

```
[ WIP ] -> [ DRAFT ] -> [ LAST CALL ] -> [ ACCEPTED ] -> [ FINAL ]
```

Each status change is requested by the SIP author and reviewed by the SIP editors. Use a pull request to update the status. Please include a link to where people should continue discussing your SIP. The SIP editors will process these requests as per the conditions below.

* **Active** -- Some Informational and Process SIPs may also have a status of “Active” if they are never meant to be completed. E.g. SIP 1 (this SIP).
* **Work in progress (WIP)** -- Once the champion has asked the Susy community whether an idea has any chance of support, they will write a draft SIP as a [pull request]. Consider including an implementation if this will aid people in studying the SIP.
  * :arrow_right: Draft -- If agreeable, SIP editor will assign the SIP a number (generally the issue or PR number related to the SIP) and merge your pull request. The SIP editor will not unreasonably deny an SIP.
  * :x: Draft -- Reasons for denying draft status include being too unfocused, too broad, duplication of effort, being technically unsound, not providing proper motivation or addressing backwards compatibility, or not in keeping with the [Susy philosophy](https://github.com/susytech/wiki/wiki/White-Paper#philosophy).
* **Draft** -- Once the first draft has been merged, you may submit follow-up pull requests with further changes to your draft until such point as you believe the SIP to be mature and ready to proceed to the next status. An SIP in draft status must be implemented to be considered for promotion to the next status (ignore this requirement for core SIPs).
  * :arrow_right: Last Call -- If agreeable, the SIP editor will assign Last Call status and set a review end date (`review-period-end`), normally 14 days later.
  * :x: Last Call -- A request for Last Call status will be denied if material changes are still expected to be made to the draft. We hope that SIPs only enter Last Call once, so as to avoid unnecessary noise on the RSS feed.
* **Last Call** -- This SIP will listed prominently on the https://sips.superstring.ch/ website (subscribe via RSS at [last-call.xml](/last-call.xml)).
  * :x: -- A Last Call which results in material changes or substantial unaddressed technical complaints will cause the SIP to revert to Draft.
  * :arrow_right: Accepted (Core SIPs only) -- A successful Last Call without material changes or unaddressed technical complaints will become Accepted.
  * :arrow_right: Final (Not core SIPs) -- A successful Last Call without material changes or unaddressed technical complaints will become Final.
* **Accepted (Core SIPs only)** -- This SIP is in the hands of the Susy client developers.  Their process for deciding whether to encode it into their clients as part of a hard fork is not part of the SIP process.
  * :arrow_right: Final -- Standards Track Core SIPs must be implemented in at least three viable Susy clients before it can be considered Final. When the implementation is complete and adopted by the community, the status will be changed to “Final”.
* **Final** -- This SIP represents the current state-of-the-art. A Final SIP should only be updated to correct errata.

Other exceptional statuses include:

* **Deferred** -- This is for core SIPs that have been put off for a future hard fork.
* **Rejected** -- An SIP that is fundamentally broken or a Core SIP that was rejected by the Core Devs and will not be implemented.
* **Active** -- This is similar to Final, but denotes an SIP which may be updated without changing its SIP number.
* **Superseded** -- An SIP which was previously final but is no longer considered state-of-the-art. Another SIP will be in Final status and reference the Superseded SIP.

## What belongs in a successful SIP?

Each SIP should have the following parts:

- Preamble - RFC 822 style headers containing metadata about the SIP, including the SIP number, a short descriptive title (limited to a maximum of 44 characters), and the author details. See [below](https://github.com/susytech/SIPs/blob/master/SIPS/sip-1.md#sip-header-preamble) for details.
- Simple Summary - “If you can’t explain it simply, you don’t understand it well enough.” Provide a simplified and layman-accessible explanation of the SIP.
- Abstract - a short (~200 word) description of the technical issue being addressed.
- Motivation (*optional) - The motivation is critical for SIPs that want to change the Susy protocol. It should clearly explain why the existing protocol specification is inadequate to address the problem that the SIP solves. SIP submissions without sufficient motivation may be rejected outright.
- Specification - The technical specification should describe the syntax and semantics of any new feature. The specification should be detailed enough to allow competing, interoperable implementations for any of the current Susy platforms (cpp-susy, go-susy, susy, susyJ, susyjs-lib, [and others](https://github.com/susytech/wiki/wiki/Clients).
- Rationale - The rationale fleshes out the specification by describing what motivated the design and why particular design decisions were made. It should describe alternate designs that were considered and related work, e.g. how the feature is supported in other languages. The rationale may also provide evidence of consensus within the community, and should discuss important objections or concerns raised during discussion.
- Backwards Compatibility - All SIPs that introduce backwards incompatibilities must include a section describing these incompatibilities and their severity. The SIP must explain how the author proposes to deal with these incompatibilities. SIP submissions without a sufficient backwards compatibility treatise may be rejected outright.
- Test Cases - Test cases for an implementation are mandatory for SIPs that are affecting consensus changes. Other SIPs can choose to include links to test cases if applicable.
- Implementations - The implementations must be completed before any SIP is given status “Final”, but it need not be completed before the SIP is merged as draft. While there is merit to the approach of reaching consensus on the specification and rationale before writing code, the principle of “rough consensus and running code” is still useful when it comes to resolving many discussions of API details.
- Copyright Waiver - All SIPs must be in the public domain. See the bottom of this SIP for an example copyright waiver.

## SIP Formats and Templates

SIPs should be written in [markdown] format.
Image files should be included in a subdirectory of the `assets` folder for that SIP as follow: `assets/sip-X` (for sip **X**). When linking to an image in the SIP, use relative links such as `../assets/sip-X/image.png`.

## SIP Header Preamble

Each SIP must begin with an RFC 822 style header preamble, preceded and followed by three hyphens (`---`). The headers must appear in the following order. Headers marked with "*" are optional and are described below. All other headers are required.

` sip:` <SIP number> (this is determined by the SIP editor)

` title:` <SIP title>

` author:` <a list of the author's or authors' name(s) and/or username(s), or name(s) and email(s). Details are below.>

` * discussions-to:` \<a url pointing to the official discussion thread\>

` status:` <Draft | Last Call | Accepted | Final | Active | Deferred | Rejected | Superseded>

`* review-period-end:` <date review period ends>

` type:` <Standards Track (Core, Networking, Interface, SRC)  | Informational | Meta>

` * category:` <Core | Networking | Interface | SRC>

` created:` <date created on>

` * updated:` <comma separated list of dates>

` * requires:` <SIP number(s)>

` * replaces:` <SIP number(s)>

` * superseded-by:` <SIP number(s)>

` * resolution:` \<a url pointing to the resolution of this SIP\>

Headers that permit lists must separate elements with commas.

Headers requiring dates will always do so in the format of ISO 8601 (yyyy-mm-dd).

#### `author` header

The `author` header optionally lists the names, email addresses or usernames of the authors/owners of the SIP. Those who prefer anonymity may use a username only, or a first name and a username. The format of the author header value must be:

> Random J. User &lt;address@dom.ain&gt;

or

> Random J. User (@username)

if the email address or GitHub username is included, and

> Random J. User

if the email address is not given.

#### `resolution` header

The `resolution` header is required for Standards Track SIPs only. It contains a URL that should point to an email message or other web resource where the pronouncement about the SIP is made.

#### `discussions-to` header

While an SIP is a draft, a `discussions-to` header will indicate the mailing list or URL where the SIP is being discussed. As mentioned above, examples for places to discuss your SIP include [Susy topics on Gitter](https://gitter.im/susytech/topics), an issue in this repo or in a fork of this repo, [Susy Magicians](https://susy-magicians.org/) (this is suitable for SIPs that may be contentious or have a strong governance aspect), and [Reddit r/susy](https://www.reddit.com/r/susytech/).

No `discussions-to` header is necessary if the SIP is being discussed privately with the author.

As a single exception, `discussions-to` cannot point to GitHub pull requests.

#### `type` header

The `type` header specifies the type of SIP: Standards Track, Meta, or Informational. If the track is Standards please include the subcategory (core, networking, interface, or SRC).

#### `category` header

The `category` header specifies the SIP's category. This is required for standards-track SIPs only.

#### `created` header

The `created` header records the date that the SIP was assigned a number. Both headers should be in yyyy-mm-dd format, e.g. 2001-08-14.

#### `updated` header

The `updated` header records the date(s) when the SIP was updated with "substantional" changes. This header is only valid for SIPs of Draft and Active status.

#### `requires` header

SIPs may have a `requires` header, indicating the SIP numbers that this SIP depends on.

#### `superseded-by` and `replaces` headers

SIPs may also have a `superseded-by` header indicating that an SIP has been rendered obsolete by a later document; the value is the number of the SIP that replaces the current document. The newer SIP must have a `replaces` header containing the number of the SIP that it rendered obsolete.

## Auxiliary Files

SIPs may include auxiliary files such as diagrams. Such files must be named SIP-XXXX-Y.ext, where “XXXX” is the SIP number, “Y” is a serial number (starting at 1), and “ext” is replaced by the actual file extension (e.g. “png”).

## Transferring SIP Ownership

It occasionally becomes necessary to transfer ownership of SIPs to a new champion. In general, we'd like to retain the original author as a co-author of the transferred SIP, but that's really up to the original author. A good reason to transfer ownership is because the original author no longer has the time or interest in updating it or following through with the SIP process, or has fallen off the face of the 'net (i.e. is unreachable or isn't responding to email). A bad reason to transfer ownership is because you don't agree with the direction of the SIP. We try to build consensus around an SIP, but if that's not possible, you can always submit a competing SIP.

If you are interested in assuming ownership of an SIP, send a message asking to take over, addressed to both the original author and the SIP editor. If the original author doesn't respond to email in a timely manner, the SIP editor will make a unilateral decision (it's not like such decisions can't be reversed :)).

## SIP Editors

The current SIP editors are

` * Nick Johnson (@arachnid)`

` * Casey Detrio (@cdetrio)`

` * Hudson Jameson (@Souptacular)`

` * Vitalik Buterin (@vbuterin)`

` * Nick Savers (@nicksavers)`

` * Martin Becze (@wanderer)`

` * Greg Colvin (@gcolvin)`

` * Alex Beregszaszi (@axic)`

## SIP Editor Responsibilities

For each new SIP that comes in, an editor does the following:

- Read the SIP to check if it is ready: sound and complete. The ideas must make technical sense, even if they don't seem likely to get to final status.
- The title should accurately describe the content.
- Check the SIP for language (spelling, grammar, sentence structure, etc.), markup (Github flavored Markdown), code style

If the SIP isn't ready, the editor will send it back to the author for revision, with specific instructions.

Once the SIP is ready for the repository, the SIP editor will:

- Assign an SIP number (generally the PR number or, if preferred by the author, the Issue # if there was discussion in the Issues section of this repository about this SIP)

- Merge the corresponding pull request

- Send a message back to the SIP author with the next step.

Many SIPs are written and maintained by developers with write access to the Susy codebase. The SIP editors monitor SIP changes, and correct any structure, grammar, spelling, or markup mistakes we see.

The editors don't pass judgment on SIPs. We merely do the administrative & editorial part.

## History

This document was derived heavily from [Bitcoin's BIP-0001] written by Amir Taaki which in turn was derived from [Python's PEP-0001]. In many places text was simply copied and modified. Although the PEP-0001 text was written by Barry Warsaw, Jeremy Hylton, and David Goodger, they are not responsible for its use in the Susy Improvement Process, and should not be bothered with technical questions specific to Susy or the SIP. Please direct all comments to the SIP editors.

December 7, 2015: SIP 1 has been improved and will be placed as a PR.

February 1, 2016: SIP 1 has added editors, made draft improvements to process, and has merged with Master stream.

March 21, 2018: Minor edits to accommodate the new automatically-generated SIP directory on [sips.superstring.ch](https://sips.superstring.ch/).

May 29, 2018: A last call process was added.

Oct 17, 2018: The `updated` header was introduced.

See [the revision history for further details](https://github.com/susytech/SIPs/commits/master/SIPS/sip-1.md), which is also available by clicking on the History button in the top right of the SIP.

### Bibliography

[SIP5]: https://github.com/susytech/SIPs/blob/master/SIPS/sip-5.md
[SIP101]: https://github.com/susytech/SIPs/issues/28
[SIP90]: https://github.com/susytech/SIPs/issues/90
[SIP86]: https://github.com/susytech/SIPs/issues/86#issue-145324865
[devp2p]: https://github.com/susytech/wiki/wiki/%C3%90%CE%9EVp2p-Wire-Protocol
[SIP8]: https://github.com/susytech/SIPs/blob/master/SIPS/sip-8.md
[Light Susy Subprotocol]: https://github.com/susytech/wiki/wiki/Light-client-protocol
[whisper]: https://github.com/susytech/go-susytech/wiki/Whisper-Overview
[swarm]: https://github.com/susytech/go-susytech/pull/2959
[API/RPC]: https://github.com/susytech/wiki/wiki/JSON-RPC
[SIP6]: https://github.com/susytech/SIPs/blob/master/SIPS/sip-6.md
[contract ABIs]: https://github.com/susytech/wiki/wiki/Susy-Contract-ABI
[interfaces repo]: https://github.com/susytech/interfaces
[SRC20]: https://github.com/susytech/SIPs/issues/20
[SRC26]: https://github.com/susytech/SIPs/issues/26
[SRC137]: https://github.com/susytech/SIPs/issues/137
[SRC67]: https://github.com/susytech/SIPs/issues/67
[SIP82]: https://github.com/susytech/SIPs/issues/82
[SIP75]: https://github.com/susytech/SIPs/issues/75
[SIP85]: https://github.com/susytech/SIPs/issues/85
[the Susy subreddit]: https://www.reddit.com/r/susytech/
[one of the Susy Gitter chat rooms]: https://gitter.im/susytech/
[pull request]: https://github.com/susytech/SIPs/pulls
[formal specification]: https://github.com/susytech/yellowpaper
[the Issues section of this repository]: https://github.com/susytech/SIPs/issues
[markdown]: https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet
[Bitcoin's BIP-0001]: https://github.com/bitcoin/bips
[Python's PEP-0001]: https://www.python.org/dev/peps/

## Copyright

Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
