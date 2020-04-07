# VxMail Product Spec

## Background & Motivation

The COVID-19 pandemic presents a significant challenge to the 2020
General Election in the United States. How can we safely hold elections when it may
be unsafe to congregate in a typical precinct? There is an emerging
consensus that one important solution will be the expansion of
vote-by-mail.

Our product hypothesis is that, in states that currently have little
vote-by-mail, the small-to-medium sized counties that process no more
than 50,000 votes are likely to have the hardest time making the
necessary adjustments. Many of those counties are lightly staffed, and
many have a completely manual process for processing absentee ballot
requests, stuffing and mailing ballots out, and finally receiving,
sorting, verifying, extracting, and scanning the returned ballots. A
manual process that works for a few hundred ballots quickly falls over
for a few thousand ballots, and establishing a more automated process
in the 6 months we have left is a huge challenge for each small county
to undertake.

We propose VxMail, a set of tools to help small counties quickly scale
up their vote-by-mail capacity.

## Key Hypothesis

A number of small and some medium-sized counties have a sufficiently
manual process for a relatively small number of vote-by-mail ballots
today. COVID-19 will cause, for them, a shift to vote-by-mail, with 10
times more ballots, which makes the manual process no longer
practical—because of insufficient speed and accuracy. With
simple COTS hardware and software, we can enable 3 election staffers
to handle 50,000 vote-by-mail ballots assuming at least 4 weeks for
sending out ballots prior to election day and 2 weeks for tabulation.

## VxMail Components

VxMail includes:
* a Mail Ballot Management System (MBMS) to send mail ballots to voters.
* a Signature Verification System (SVS) to check signatures on incoming ballots.
* tools to efficiently open envelopes and extract ballots.
* a Ballot Scanning System (BSS) to scan and tabulate ballots.

Only the MBMS is online for connecting with print&mail services, while
the other systems are offline for security purposes.

### Mail Ballot Management System: printing & mailing ballots

VxMail includes a _Mail Ballot Management System (MBMS)_ where an
election official can:

* upload an election definition
* upload a mailing list
* proof ballots
* order ballots to be printed and mailed
* track ballot delivery to voters.
* track ballot return from voters.

All ballot printing, stuffing, and mailing is automated. Voters
receives a ballot and return envelope, including a signature box.

### Signature Verification System

When ballots are received, VxMail lets election officials verify
signatures as follows:

* a state export of voter IDs and signatures is loaded into the VxMail Signature Verification System (SVS)
* Ballot envelopes are scanned via the SVS scanner in small batches. On screen, expected and actual signatures are displayed for confirmation by election officials. If any of the batch are a non-match, SVS pauses while that ballot envelope is set aside. Scanning then continues, one small batch at a time.
* When all ballots have been scanned, an export of successful and unsuccessful voter IDs is generated for upload into the state voter management system to record that those voters have cast a ballot.

### Envelope Opening & Extraction

Depending on the size of the county, an off-the-shelf automated
envelope opener can be used. Alternatively, a simple envelope cutter
is most cost-effective for smaller counties.

### Ballot Scanning System

Extracted ballots are tabulated via the VxMail Ballot Scanning System
(BSS). Three scanner models are available depending on the county size:

* small: up to 10,000 ballot pages per day, in batches of 50, each batch taking 1 minute to scan.
* medium: up to 45,000 ballot pages per day, in batches of 300, each batch taking 3 minutes to scan.
* large: up to 120,000 ballot pages per day, in batches of 500, each batch taking 3.5 minutes to scan.

The BSS then produces a set of CVRs, which can also be tabulated.

## Future Components Under Consideration

VxMail may include additional components based on the needs we hear from states and counties:

* an online absentee ballot request system to let voters request an absentee ballot.
* a mail-and-SMS-based signature cure process, where invalid signatures can be remedied efficiently.

## Cost

Our rough estimate of complete equipment system cost is:

* Small: $3,500
* Medium: $7,000
* Large: $15,000

Plus, for ballot printing and mailing: $2.50 per voter, not including return postage.
