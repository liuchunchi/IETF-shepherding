# SATP-architecture Shepherd Write-Up

As required by [RFC 4858](https://www.rfc-editor.org/rfc/rfc4858.txt) and requested by the SATP WG, this is the shepherd write-up of SATP-architecture document using the most current template I found at [here](https://datatracker.ietf.org/doc/shepherdwriteup-template/individual).


## Document History
1. Does the working group (WG) consensus represent the strong concurrence of a
few individuals, with others being silent, or did it reach broad agreement?

    This document has been discussed in nearly all SATP sessions at past IETF meetings. On February 4, 2025, the chairs called on the working group to review the document and submit feedback. For the SATP-architecture document, the following responses were received:

    * 2 reviews with suggested changes (Hadarker and Willman)
    * 23 reviews with explicit support. 

    Before that, there are [4](https://github.com/ietf-satp/draft-ietf-satp-architecture/pulls?q=is%3Apr+is%3Aclosed) closed PRs related to reviews and fixes; yet 2 people are involved. Maybe there's more off-github.

2. Was there controversy about particular points, or were there decisions where
the consensus was particularly rough?

    No. The consensus within the working group on this document was reached unroughly.

3. Has anyone threatened an appeal or otherwise indicated extreme discontent? If
so, please summarize the areas of conflict in separate email messages to the
responsible Area Director. (It should be in a separate email because this
questionnaire is publicly available.)

    None noticed.

4. For protocol documents, are there existing implementations of the contents of
the document? Have a significant number of potential implementers indicated
plans to implement? Are any existing implementations reported somewhere,
either in the document itself (as RFC 7942 recommends) or elsewhere
(where)?

    One of the main editor's affiliation -- IBM, has a [Hyperledger Cacti implementation](https://hyperledger-cacti.github.io/cacti/).

## Additional Reviews

5. Do the contents of this document closely interact with technologies in other
IETF working groups or external organizations, and would it therefore benefit
from their review? Have those reviews occurred? If yes, describe which
reviews took place.

    Since the document defines a new architecture, an SEC directorate early review is requested, and the [result](https://datatracker.ietf.org/doc/review-ietf-satp-architecture-05-secdir-early-orman-2024-07-14/) is NOT READY.

    He explicitly mentioned a few problems/questions:

    * The reviewer interprets that banking is the main use case. In which case, he is not sure if the architecture is secure enough for implementing finance-level systems.
    * The reviewer is concerned of double-spending/transfer problem that may be caused by possible attacks. In other words, he is not sure if the crash recovery mechanism guarantees asset transfer atomicity.
    * The reviewer is not clear about address discoverability issues-- "Are the transaction originator and the beneficiary be required to have addresses in the same ASN as their respective gateways? Is the gateway required to have an address in the same ASN as the rest of transaction processing network?"
    * The reviewer is not clear about the verifiability issues--  if the "cryptographic proofs that an asset has been burned or minted" be necessary and should not be out of scope of this document? How to ensure that an "authorized third party" can carry out a verification of the transfer?
    * Should the liveness and third-party verification be part of desirable properties?

    There are no known reviews from other WGs.

6. Describe how the document meets any required formal expert review criteria,
such as the MIB Doctor, YANG Doctor, media type, and URI type reviews.

    At April 15, Wes provided a [review](https://mailarchive.ietf.org/arch/msg/sat/jGHdIP2s9e1OboQnvvWxonp2fjs/). He mentioned the document should not rely much on legal bindings-- the protocol should stand on its own technically. These "legal" related references should be removed.

7. If the document contains a YANG module, has the final version of the module
been checked with any of the recommended validation tools for syntax and
formatting validation? If there are any resulting errors or warnings, what is
the justification for not fixing them at this time? Does the YANG module
comply with the Network Management Datastore Architecture (NMDA) as specified
in RFC 8342?

    The document does not contain a YANG module.

8. Describe reviews and automated checks performed to validate sections of the
final version of the document written in a formal language, such as XML code,
BNF rules, MIB definitions, CBOR's CDDL, etc.

    The shepherd does not find related automated checks in the document homepage, as they usually being provided in the "additional resources" in the document homepage.

## Document Shepherd Checks
9. Based on the shepherd's review of the document, is it their opinion that this
document is needed, clearly written, complete, correctly designed, and ready
to be handed off to the responsible Area Director?

    According to the SEC early review, some security considerations should be presented more straightforwardly to deliver security guaratees.

10. Several IETF Areas have assembled lists of common issues that their
reviewers encounter. For which areas have such issues been identified
and addressed? For which does this still need to happen in subsequent
reviews?

11. What type of RFC publication is being requested on the IETF stream (Best
Current Practice, Proposed Standard, Internet Standard,
Informational, Experimental or Historic)? Why is this the proper type
of RFC? Do all Datatracker state attributes correctly reflect this intent?

    Informational. Because it is an architectural framework.

12. Have reasonable efforts been made to remind all authors of the intellectual
property rights (IPR) disclosure obligations described in BCP 79? To
the best of your knowledge, have all required disclosures been filed? If
not, explain why. If yes, summarize any relevant discussion, including links
to publicly-available messages when applicable.

    No.
    The shepherd searched the email archive with keywords like "IPR", "disclosure", "patent", none came out. It seems the chairs didn't call for IPR disclosure.

13. Has each author, editor, and contributor shown their willingness to be
listed as such? If the total number of authors and editors on the front page
is greater than five, please provide a justification.

    No issue discovered.

14. Document any remaining I-D nits in this document. Simply running the idnits
tool is not enough; please review the "Content Guidelines" on
authors.ietf.org. (Also note that the current idnits tool generates
some incorrect warnings; a rewrite is underway.)

    ** The document seems to lack an IANA Considerations section.  (See Section
        2.2 of https://www.ietf.org/id-info/checklist for how to handle the case
        when there are no actions for IANA.)

    ** There are 4 instances of too long lines in the document, the longest one
        being 1 character in excess of 72.

    It is note mentioning the document references have a lot of nits, undefined cites, unused cites, incorrect cites... For page conciseness, I leave the link [here](https://author-tools.ietf.org/api/idnits?url=https://www.ietf.org/archive/id/draft-ietf-satp-architecture-06.txt).

15. Should any informative references be normative or vice-versa? See the IESG
Statement on Normative and Informative References.

    None.

16. List any normative references that are not freely available to anyone. Did
the community have sufficient access to review any such normative
references?

    ISO standards are not freely available. 2 ISO standard are referenced.
    
    The authors also references 6 ACM/IEEE/... academic papers, which could require membership to acquire.

17. Are there any normative downward references (see RFC 3967 and BCP 1)  that are not already listed in the DOWNREF registry? If so,
list them.

18. Are there normative references to documents that are not ready to be
submitted to the IESG for publication or are otherwise in an unclear state?
If so, what is the plan for their completion?

    draft-belchior-satp-gateway-recovery-02 is referenced. Plan for completion is unknown.

19. Will publication of this document change the status of any existing RFCs? If
so, does the Datatracker metadata correctly reflect this and are those RFCs
listed on the title page, in the abstract, and discussed in the
introduction? If not, explain why and point to the part of the document
where the relationship of this document to these other RFCs is discussed.

    No.

20. Describe the document shepherd's review of the IANA considerations section,
especially with regard to its consistency with the body of the document.
Confirm that all aspects of the document requiring IANA assignments are
associated with the appropriate reservations in IANA registries. Confirm
that any referenced IANA registries have been clearly identified. Confirm
that each newly created IANA registry specifies its initial contents,
allocations procedures, and a reasonable name (see RFC 8126).

    There is no IANA considerations section.

21. List any new IANA registries that require Designated Expert Review for
future allocations. Are the instructions to the Designated Expert clear?
Please include suggestions of designated experts, if appropriate.
