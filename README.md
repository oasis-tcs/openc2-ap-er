![OpenC2](images/er-ap-logo-header.png)

## ![oasis-avatar](https://avatars.githubusercontent.com/u/47402065?s=24&v=4) An OASIS [Work Product](https://www.oasis-open.org/policies-guidelines/oasis-defined-terms-2018-05-22/#dWorkProduct) Repository ![oasis-avatar](https://avatars.githubusercontent.com/u/47402065?s=24&v=4) 

Members of the OASIS [Open Command and Control (OpenC2) Technical
Committee](https://www.oasis-open.org/committees/tc_home.php?wg_abbrev=openc2)
use this GitHub repository as part of the [TC's chartered
work](https://www.oasis-open.org/committees/openc2/charter.php).
Contributors must be Members of the TC. Work is governed by the
OASIS policies and is not done under typical open source
licensing. For more details, see the
[Contributions](#contributions) and [Licensing](#licensing)
sections below. 

## :blue_book: _OpenC2 Actuator Profile for Endpoint Response_ :blue_book:

Endpoint Detection and Response (EDR) technologies provide a
means for continuous endpoint monitoring and analysis to more
readily identify, detect, mitigate and remediate, or prevent
advanced threats. This OpenC2 Actuator Profile defines the
Actions, Targets, Specifiers and Options that are consistent with
the version 1.0 of the [OpenC2 Language
Specification](https://docs.oasis-open.org/openc2/oc2ls/v1.0/oc2ls-v1.0.html)
in the context of command and control of various endpoint
response technologies.

### :twisted_rightwards_arrows: Repository Organization :twisted_rightwards_arrows:

![branches](images/repo-branches.png)

OpenC2 work product repositories are organized a bit differently
than typical open source software project repositories:

* The **Published** (default) branch represents the current,
  stable, approved version of the work product. If the product
  hasn't progressed past an [OASIS Committee Specification Draft
  (CSD)](https://www.oasis-open.org/policies-guidelines/tc-process-2017-05-26/#committeeDraft),
  this branch is essentially empty
* The **Working** branch is where all work-in-progress content is
  captured, and is the place to go for the [current working
  version](https://github.com/oasis-tcs/openc2-ap-er/blob/working/oc2pf.md)
  of this work product

More information about the TC's repository organizing conventions
and branching strategy can be found in our [Documentation
Norms](https://github.com/oasis-tcs/openc2-tc-ops/blob/main/Documentation-Norms.md#433-configure-repository).

###  :left_speech_bubble: Description  :left_speech_bubble:

An Endpoint Detection and Response (EDR) system is a security
mechanism which identifies malicious behaviours by recording
system activities and comparing them to sets of signatures or
heuristics. EDR systems facilitate in digital forensics and
incident response by storing and indexing said events, as well as
provide functionality to respond to security incidents as they
pertain to actively exploited, infected or vulnerable endpoints.

OpenC2 has elected to separate the endpoint response (ER) portion
of EDR from other aspects.  This Actuator profile specifies the
set of Actions, Targets, Specifiers, and Command Arguments that
integrates ER functionality with the OpenC2 Command set. Through
this Command set, cyber security orchestrators may gain
visibility into and provide control over the ER functionality in
a manner that is independent of the instance of the EDR
implementation.

###  :writing_hand: Contributions  :writing_hand:
<div>
<p>As stated in this repository's <a href="CONTRIBUTING.md">CONTRIBUTING file</a>, contributors to this repository are expected to be Members of the OASIS OpenC2 TC, for any substantive change requests.  Anyone wishing to contribute to this GitHub project and <a href="https://www.oasis-open.org/join/participation-instructions">participate</a> in the TC's technical activity is invited to join as an OASIS TC Member.  Public feedback is also accepted, subject to the terms of the <a href="https://www.oasis-open.org/policies-guidelines/ipr#appendixa">OASIS Feedback License</a>.</p>
</div>


###  :scroll: Licensing  :scroll:

<div>
<p>Please see the <a href="LICENSE.md">LICENSE</a> file for description of the license terms and OASIS policies applicable to the TC's work in this GitHub project. Content in this repository is intended to be part of the OpenC2 TC's permanent record of activity, visible and freely available for all to use, subject to applicable OASIS policies, as presented in the repository <a href="LICENSE.md">LICENSE</a> file.</p>
</div>


###  :left_speech_bubble: Further Description of this Repository  :left_speech_bubble:
<div>
<p>Members of the <a href="https://www.oasis-open.org/committees/openc2/">OASIS Open Command and Control (OpenC2) TC</a> create and manage technical content in this TC GitHub repository ( <a href="https://github.com/oasis-tcs/openc2-ap-er">https://github.com/oasis-tcs/openc2-ap-er</a> ) as part of the TC's chartered work (<i>i.e.</i>, the program of work and deliverables described in its <a href="https://www.oasis-open.org/committees/openc2/charter.php">charter</a>).</p>

<p>OASIS TC GitHub repositories, as described in <a href="https://www.oasis-open.org/resources/tcadmin/github-repositories-for-oasis-tc-members-chartered-work">GitHub Repositories for OASIS TC Members' Chartered Work</a>, are governed by the OASIS <a href="https://www.oasis-open.org/policies-guidelines/tc-process">TC Process</a>, <a href="https://www.oasis-open.org/policies-guidelines/ipr">IPR Policy</a>, and other policies, similar to TC Wikis, TC JIRA issues tracking instances, TC SVN/Subversion repositories, etc.  While they make use of public GitHub repositories, these TC GitHub repositories are distinct from <a href="https://www.oasis-open.org/resources/open-repositories">OASIS Open Repositories</a>, which are used for development of open source <a href="https://www.oasis-open.org/resources/open-repositories/licenses">licensed</a> content.</p>
</div>


### :envelope_with_arrow: Contact :envelope_with_arrow:
<div>
<p>Please send questions or comments about <a href="https://www.oasis-open.org/resources/tcadmin/github-repositories-for-oasis-tc-members-chartered-work">OASIS TC GitHub repositories</a> to the <a href="mailto:tc-admin@oasis-open.org">OASIS TC Administrator</a>.  For questions about content in this repository, please contact the TC Chair or Co-Chairs as listed on the the <tc short name> TC's <a href="https://www.oasis-open.org/committees/tc_home.php?wg_abbrev=openc2">home page</a>.</p>
</div>

