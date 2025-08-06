# SATP-core Shepherd Write-Up

As required by [RFC 4858](https://www.rfc-editor.org/rfc/rfc4858.txt) and requested by the SATP WG, this is the shepherd write-up of SATP-core document using the most current template I found at [here](https://datatracker.ietf.org/doc/shepherdwriteup-template/individual).


## Document History
1. Does the working group (WG) consensus represent the strong concurrence of a
few individuals, with others being silent, or did it reach broad agreement?

    This document has been discussed in nearly all SATP sessions at past IETF meetings. On February 4, 2025, the chairs called on the working group to review the document and submit feedback. For the SATP-core document, the following responses were received:

    * 2 reviews with suggested changes (Hadarker and Willman)
    * 23 reviews with explicit support. 

    Before that, there are [20](https://github.com/ietf-satp/draft-ietf-satp-core/pulls?q=is%3Apr+is%3Aclosed) closed PRs related to reviews and fixes; about 6~7ish people are involved.

2. Was there controversy about particular points, or were there decisions where
the consensus was particularly rough?

    No.

    As of May 30, some points are under discussion, but not blockers:
    * SATP-core document need minimum MUST requirements for better interoperability. Specifically, the JSON message should be mandatorily signed using JWS mechanisms? A MUST-implement curve/ciphersuite? The tendency of consensus is yes-- use JWS with ECDSA over P256 curve with SHA-256 as the signing algorithm.

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

    Since the document defines an application-layer SATP core message exchanged between two gateways, this document would benefit from a HTTP directorate review. A HTTP directorate early review is requested, and the [result](https://datatracker.ietf.org/doc/review-ietf-satp-core-00-httpdir-early-pardue-2023-04-28/) is NOT READY.

    He explicitly mentioned a few problems:

    * The document has left important interoperability questions answered (might refer to section 5, SATP core message format). If the document is developed based on external documentations of some existing projects, the document should reference it. Otherwise some clarification on the specification is needed. The WG is currently discussing this issue.
    * The document has some duplication with SATP-architecture. He recommend to reduce redundancy to make "the protocol specification clearer to review."
    * The reviewer thinks the JSON messages defined in this document should be just message payloads, but it appears some messages also include HTTP semantics. This problem is especially obvious for Type-1 API. Is this supposed to define a new/custom HTTP encapsulation? If so, it "needs deeper discussion and engagement".
    * Other ambiguity or editorial nits.

    There are no known reviews from other WGs.

6. Describe how the document meets any required formal expert review criteria,
such as the MIB Doctor, YANG Doctor, media type, and URI type reviews.

    At April 15, Wes provided a [review](https://mailarchive.ietf.org/arch/msg/sat/myjl2gZ1emR4JuGObSJKHE6IswE/). He mentioned: The document "need the enumeration of possible values for restricted protocol components that really need an exact value agreed to by both sides", which could help disambiguate future implementation process using this proposed RFC. The shepherd infer that this reflects the similar ambiguity issues raised by the HTTP Directorate reivew above. Some other editorial nits are mentioned.

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

    According to the HTTP early review, there are certain specification ambiguity issues that need some fixes.

10. Several IETF Areas have assembled lists of common issues that their
reviewers encounter. For which areas have such issues been identified
and addressed? For which does this still need to happen in subsequent
reviews?

11. What type of RFC publication is being requested on the IETF stream (Best
Current Practice, Proposed Standard, Internet Standard,
Informational, Experimental or Historic)? Why is this the proper type
of RFC? Do all Datatracker state attributes correctly reflect this intent?

    Proposed Standard. 
    
    Because it defines the core SATP message format to be exchanged between two gateways.

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

    == There are 3 instances of lines with non-ascii characters in the document.

    == The page length should not exceed 58 lines per page, but there was 3
        longer pages, the longest (page 12) being 71 lines

15. Should any informative references be normative or vice-versa? See the IESG
Statement on Normative and Informative References.

    None.

16. List any normative references that are not freely available to anyone. Did
the community have sufficient access to review any such normative
references?

    None discovered.

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

    The authors left IANA considerations section as TBD.

21. List any new IANA registries that require Designated Expert Review for
future allocations. Are the instructions to the Designated Expert clear?
Please include suggestions of designated experts, if appropriate.
