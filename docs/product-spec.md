# VxMail Product Spec

## Background & Motivation

The COVID-19 pandemic presents a new and significant challenge to the 2020
General Election in the United States. How can we safely hold elections when it may
be unsafe to congregate in a typical precinct? There is an emerging
consensus that one important solution will be the expansion of
vote-by-mail.

## Key Hypothesis

Today, many small and some medium-sized election jurisdictions
(counties, towns, parishes, ...) have a manual process for handling a
relatively small number of vote-by-mail ballots. COVID-19 will require
those jurisdictions to process many more mail ballots than they're
accustomed to. Given limited time and people-power, the manual
processes will be impractical.

By offering simple, readily available, off-the-shelf hardware and
robust software, we can enable 3 election staffers to manage mailing
and receiving 50,000 ballots.

## VxMail

We propose VxMail, a set of tools to help small jurisdictions quickly scale
up their vote-by-mail capacity.

### Components

VxMail includes:
- a Ballot Manager to create and proof mail ballots, schedule printing
  and mailing, log receipt of returned ballots, and verify voter
  signatures.
- tools to efficiently open envelopes and extract ballots.
- a Ballot Tabulator to scan and tabulate ballots.

The Ballot Manager works online for connecting with print-and-mail
services, and potentially to the state's Election Management
System. The Ballot Tabulator is offline for security purposes.

### Proofing, Printing, and Mailing Ballots

The VxMail Ballot Manager lets an election official:

- upload the election definition
- proof generated ballots on screen
- upload the voter mailing list (name, mailing address, voter ID, ballot style)
- order those ballots printed and mailed, with a 3-day mailing turnaround.
- track ballot delivery to voters
- track ballot return from voters

All ballot printing, stuffing, and mailing is managed by VotingWorks
and its partners, while election officials can track that process via
the Ballot Manager. Voters receives a ballot and return envelope,
including, as per best practices, a clear location to sign printed on
the return envelope.

### Verifying Voter Signatures

When ballots are received, election officials can verify ballot
envelope signatures using the VxMail Ballot Manager, which includes an
envelope scanner:

- An export of voter IDs and signatures, provided by the state, is
  loaded into the VxMail Ballot Manager prior to the election and
  updated as necessary.
- Ballot envelopes are scanned into the Ballot Manager in small
  batches. On screen, expected and actual signatures are displayed for
  confirmation by election officials. If election officials detect any
  mismatch on screen, they indicate this with a single tap on the
  corresponding button, and the scanning process pauses while election
  officials locate and set aside that ballot envelope. VxMail records
  digitally that this envelope was rejected. Scanning ballot envelopes
  continues, one small batch at a time, and rejected envelopes can be
  further adjudicated as necessary.
- When all ballots have been scanned, the VxMail Ballot Manager
  produces an export of all ballots received, along with accepted and
  rejected voter signatures, including digital images for both sides
  of the corresponding ballot envelopes. These can then be uploaded
  into the state voter management system to record that those voters
  have cast a ballot.

If integration with the state's Election Management System is not an
option, election officials may instead use their existing Election
Management System and look up voter records as ballot envelopes come
in, either by scanning a voter ID barcode that appears on the ballot
return envelope, or by manually looking up the voter record.

### Opening Envelopes and Extracting Ballots

For larger jurisdictions, VxMail includes an off-the-shelf automatic
envelope opener and letter extractor, reducing the personnel needed
for opening envelopes and extracting ballots. For smaller
jurisdictions, VxMail includes an affordable automatic letter opener,
and ballots are extracted manually.

### Scanning and Tabulating Ballots

Extracted ballots are tabulated via the Ballot Tabulator, which
includes a physical scanner and an accompanying laptop. Three scanner
models are available depending on the jurisdiction size:

- small: up to 10,000 ballot pages per day, in batches of 50, each batch taking 1 minute to scan.
- medium: up to 45,000 ballot pages per day, in batches of 300, each batch taking 3 minutes to scan.
- large: up to 120,000 ballot pages per day, in batches of 500, each batch taking 3.5 minutes to scan.

The VxMail Tabulator produces a set of cast vote records (CVRs) and a
tally of those CVRs.

### Ballot Reconciliation

Election officials can use VxMail to ensure that each voter casts no
more than one ballot. The VxMail Ballot Manager tracks the list of
voters who have cast a ballot, which can then be reconciled against
the state voter registration system to flag any voter that may have
cast a ballot both in person and by mail. Election officials have a
choice of two options:
- connecting the VxMail Ballot Manager to the State Election
  Management System for live information on which voters have alreay
  voted.
- reconciling the VxMail Ballot Manager received-ballot list with the
  Election Management System on a nightly basis, leaving ballot
  envelopes unopened until the next day once those voters have been
  confirmed not to have voted by other means.

## Future Components Under Consideration

VxMail may include additional components based on the needs we hear from local election officials:

- an online absentee ballot request system to let voters request an absentee ballot.
- a multi-channel signature cure process, where invalid signatures can be remedied efficiently.

## Cost

Our rough estimate of complete equipment system cost is:

- Small: $3,500
- Medium: $7,000
- Large: $15,000

Plus, for ballot printing and mailing: $2.00 per voter, *including return postage*.
