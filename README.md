# Indy Improvement Intiatives (RFCs)
[Indy IIIs]: #indy-iiis

Many changes, including bug fixes and documentation improvements can be
implemented and reviewed via Jira Issues and a normal GitHub pull request workflow.

Some changes though are "substantial", and we ask that these be put through a
bit of a design process and produce a consensus among the Indy community and
the [sub-team]s.

The Indy Improvement Initiative "iii" process is intended to provide a consistent
and controlled path for new features to enter the language and standard
libraries, so that all stakeholders can be confident about the direction the
language is evolving in.


## Table of Contents
[Table of Contents]: #table-of-contents

  - [Opening](#indy-iiis)
  - [Table of Contents]
  - [When you need to follow this process]
  - [Before creating an III]
  - [What the process is]
  - [The III life-cycle]
  - [Reviewing IIIs]
  - [Implementing an III]
  - [III Postponement]
  - [Help this is all too informal!]
  - [License]
  - [Credits]


## When you need to follow this process
[When you need to follow this process]: #when-you-need-to-follow-this-process

You need to follow this process if you intend to make "substantial" changes to
Indy node, Indy SDK interfaces, Indy Crypto, the Anoncreds protocol, 
Agent communication protocols or the RFC process itself. What constitutes a
"substantial" change is evolving based on community norms and varies depending
on what part of the system you are proposing to change, but may include the
following.

  - Anything that could break existing APIs or clients.
  - Changing parts of the cryptography or protocols.
  - Anything affecting consensus
  - Changes to permissioning or privacy characteristics of the system.
  - Other feature additions that require architecture explainations or documentation.

Some changes do not require an RFC:

  - Rephrasing, reorganizing, refactoring, or otherwise "changing shape does
    not change meaning".
  - Additions that strictly improve objective, numerical quality criteria
    (warning removal, speedup, better platform coverage, more parallelism, trap
    more errors, etc.)
  - Additions only likely to be _noticed by_ other developers-of-indy,
    invisible to users-of-indy.

If you submit a pull request to implement a new feature without going through
the III process, it may be closed with a polite request to submit an III first.


### Sub-team specific guidelines
[Sub-team specific guidelines]: #sub-team-specific-guidelines

For more details on when an III is required for the following areas, please see
the Indy community's [sub-team] specific guidelines for:

  - [node changes](node_changes.md),
  - [sdk changes](sdk_changes.md),
  - [cryptography changes](crypto_changes.md).


## Before creating an iii
[Before creating an iii]: #before-creating-an-iii

A hastily-proposed III can hurt its chances of acceptance. Low quality
proposals, proposals for previously-rejected features, or those that don't fit
into the near-term roadmap, may be quickly rejected, which can be demotivating
for the unprepared contributor. Laying some groundwork ahead of the III can
make the process smoother.

Although there is no single way to prepare for submitting an III, it is
generally a good idea to pursue feedback from other project developers
beforehand, to ascertain that the III may be desirable; having a consistent
impact on the project requires concerted effort toward consensus-building.

The most common preparations for writing and submitting an III include talking
the idea over on #indy in Hyperledger Rocket.Chat, discussing the topic on our 
[mailing list], and occasionally posting "pre-IIIs" on the mailing list. You 
may file issues on this repo for discussion, but these are not actively looked 
at by the teams.

As a rule of thumb, receiving encouraging feedback from long-standing project
developers, and particularly members of the relevant [sub-team] is a good
indication that the III is worth pursuing.


## What the process is
[What the process is]: #what-the-process-is

In short, to get a major feature added to Indy, one must first get the III
merged into the III repository as a markdown file. At that point the III is
"active" and may be implemented with the goal of eventual inclusion into Indy.

  - Fork the indy-rfc repo [III repository]
  - Copy `0000-template.md` to `text/0000-my-feature.md` (where "my-feature" is
    descriptive. don't assign an III number yet).
  - Fill in the III. Put care into the details: IIIs that do not present
    convincing motivation, demonstrate understanding of the impact of the
    design, or are disingenuous about the drawbacks or alternatives tend to be
    poorly-received.
  - Submit a pull request. As a pull request the III will receive design
    feedback from the larger community, and the author should be prepared to
    revise it in response.
  - Each pull request will be labeled with the most relevant [sub-team], which
    will lead to its being triaged by that team in a future meeting and assigned
    to a member of the subteam.
  - Build consensus and integrate feedback. IIIs that have broad support are
    much more likely to make progress than those that don't receive any
    comments. Feel free to reach out to the III assignee in particular to get
    help identifying stakeholders and obstacles.
  - The sub-team will discuss the III pull request, as much as possible in the
    comment thread of the pull request itself. Offline discussion will be
    summarized on the pull request comment thread.
  - IIIs rarely go through this process unchanged, especially as alternatives
    and drawbacks are shown. You can make edits, big and small, to the III to
    clarify or change the design, but make changes as new commits to the pull
    request, and leave a comment on the pull request explaining your changes.
    Specifically, do not squash or rebase commits after they are visible on the
    pull request.
  - At some point, a member of the subteam will propose a "motion for final
    comment period" (FCP), along with a *disposition* for the III (merge, close,
    or postpone).
    - This step is taken when enough of the tradeoffs have been discussed that
    the subteam is in a position to make a decision. That does not require
    consensus amongst all participants in the III thread (which is usually
    impossible). However, the argument supporting the disposition on the III
    needs to have already been clearly articulated, and there should not be a
    strong consensus *against* that position outside of the subteam. Subteam
    members use their best judgment in taking this step, and the FCP itself
    ensures there is ample time and notification for stakeholders to push back
    if it is made prematurely.
    - For IIIs with lengthy discussion, the motion to FCP is usually preceded by
      a *summary comment* trying to lay out the current state of the discussion
      and major tradeoffs/points of disagreement.
    - Before actually entering FCP, *all* members of the subteam must sign off;
    this is often the point at which many subteam members first review the III
    in full depth.
  - The FCP lasts ten calendar days, so that it is open for at least 5 business
    days. It is also advertised widely,
    e.g. in [This Week in Indy](https://blog.sovrin.org/this-week-in-indy/). This way all
    stakeholders have a chance to lodge any final objections before a decision
    is reached.
  - In most cases, the FCP period is quiet, and the III is either merged or
    closed. However, sometimes substantial new arguments or ideas are raised,
    the FCP is canceled, and the RFC goes back into development mode.

## The III life-cycle
[The III life-cycle]: #the-iii-life-cycle

Once an III becomes "active" then authors may implement it and submit the
feature as a pull request to the appropriate Indy repos. Being "active" is 
not a rubber stamp, and in particular still does not mean the feature will 
ultimately be merged; it does mean that in principle all the major stakeholders
have agreed to the feature and are amenable to merging it.

Furthermore, the fact that a given III has been accepted and is "active"
implies nothing about what priority is assigned to its implementation, nor does
it imply anything about whether an Indy developer has been assigned the task of
implementing the feature. While it is not *necessary* that the author of the
III also write the implementation, it is by far the most effective way to see
an III through to completion: authors should not expect that other project
developers will take on responsibility for implementing their accepted feature.

Modifications to "active" IIIs can be done in follow-up pull requests. We
strive to write each III in a manner that it will reflect the final design of
the feature; but the nature of the process means that we cannot expect every
merged III to actually reflect what the end result will be at the time of the
next major release.

In general, once accepted, IIIs should not be substantially changed. Only very
minor changes should be submitted as amendments. More substantial changes
should be new IIIs, with a note added to the original III. Exactly what counts
as a "very minor change" is up to the sub-team to decide; check
[Sub-team specific guidelines] for more details.


## Reviewing IIIs
[Reviewing IIIs]: #reviewing-iiis

While the III pull request is up, the sub-team may schedule meetings with the
author and/or relevant stakeholders to discuss the issues in greater detail,
and in some cases the topic may be discussed at a sub-team meeting. In either
case a summary from the meeting will be posted back to the III pull request.

A sub-team makes final decisions about IIIs after the benefits and drawbacks
are well understood. These decisions can be made at any time, but the sub-team
will regularly issue decisions. When a decision is made, the III pull request
will either be merged or closed. In either case, if the reasoning is not clear
from the discussion in thread, the sub-team will add a comment describing the
rationale for the decision.


## Implementing an III
[Implementing an III]: #implementing-an-iii

Some accepted IIIs represent vital features that need to be implemented right
away. Other accepted IIIs can represent features that can wait until some
arbitrary developer feels like doing the work. Every accepted III should have 
an associated issue tracking its implementation in an Indy Jira project; thus that
associated issue can be assigned a priority via the triage process that the
team uses for all issues in their Jira repository.

The author of an III is not obligated to implement it. Of course, the III
author (like any other developer) is welcome to post an implementation for
review after the III has been accepted.

If you are interested in working on the implementation for an "active" III, but
cannot determine if someone else is already working on it, feel free to ask
(e.g. by leaving a comment on the associated issue).


## III Postponement
[III Postponement]: #iii-postponement

Some III pull requests are tagged with the "postponed" label when they are
closed (as part of the rejection process). An III closed with "postponed" is
marked as such because we want neither to think about evaluating the proposal
nor about implementing the described feature until some time in the future, and
we believe that we can afford to wait until then to do so. Currently,
"postponed" is used to postpone features until after Hyperledger General 
Availability. Postponed pull requests may be re-opened when the time is right. 
We don't have any formal process for that, you should ask members of the 
relevant sub-team.

Usually an III pull request marked as "postponed" has already passed an
informal first round of evaluation, namely the round of "do we think we would
ever possibly consider making this change, as outlined in the III pull request,
or some semi-obvious variation of it." (When the answer to the latter question
is "no", then the appropriate response is to close the III, not postpone it.)


### Help this is all too informal!
[Help this is all too informal!]: #help-this-is-all-too-informal

The process is intended to be as lightweight as reasonable for the present
circumstances. As usual, we are trying to let the process be driven by
consensus and community norms, not impose more structure than necessary.


[indy mailing list]: https://lists.hyperledger.org/mailman/listinfo/hyperledger-indy
[RFC issue tracker]: https://github.com/rust-lang/rfcs/issues
[III repository]: http://github.com/hyperledger/indy-rfc
[sub-team]: http://github.com/hyperledger/indy-rfc/0010-sub-teams.md

## License
[License]: #license

This repository is currently licensed under the

* Apache License, Version 2.0, ([LICENSE-APACHE](LICENSE-APACHE) or http://www.apache.org/licenses/LICENSE-2.0)

### Contributions

Unless you explicitly state otherwise, any contribution intentionally submitted for inclusion in the work by you, as defined in the Apache-2.0 license, shall be licensed as above, without any additional terms or conditions.

### Credits

This document was derived from the Rust RFC process found at https://github.com/rust-lang/rfcs.  The Rust project and its developers are not responsible for the III process or its content.  If you have questions about Indy Improvement Initiatives or the Indy Improvement Initiative process please start discussions on the Hyperledger Indy mailing list or log an issue at https://jira.hyperledger.org/projects/INDY and add it to the "Process" Epic.
