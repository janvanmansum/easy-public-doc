Depositing in EASY with SWORD v2.0
==================================

Overview
--------
Depositing in EASY via the SWORD v2.0 protocol is basically a two-phase process:

1. Submitting a deposit for ingest.
2. Tracking the state of the deposit as it goes through the ingest-flow, until it reaches ARCHIVED status.

The following diagram details this a bit further.

![overview](img/sword2.png)

1. Client creates a deposit package.
2. Client sends deposit package to SWORD Service, getting back a URL to track the deposit's state.
3. SWORD Service unzips and validates deposit.
4. EASY Ingest Flow performs checks and transformations and creates a dataset in Archival Storage.
5. EASY Ingest Flow reports back success or failure to SWORD Service.

3-5. During this time the Client periodically checks the deposit state through the URL received in step 2. If the final state of `ARCHIVED` is
reached, the process is concluded successfully. Other outcomes may be `INVALID` (the package did not meet the requirements of the SWORD service) 
or `REJECTED` (the package did not meet the requirements of the EASY Ingest Flow).

### Example Code
The following specifications may be easier to follow if you have a look at the [SWORD v2.0 client examples].

[SWORD v2.0 client examples]: https://github.com/DANS-KNAW/easy-sword2-dans-examples

SWORD
-----
### About the SWORD v2.0 Protocol

From the [SWORD website]:

> SWORD is a lightweight protocol for depositing content from one location to another.
> It stands for Simple Web-service Offering Repository Deposit and is a profile of the 
> Atom Publishing Protocol (known as APP or ATOMPUB). 

The [specifications of SWORD v2.0] build on those of [Atom] and [AtomPub]. AtomPub in turn builds on
[HTTP]. It is, however, not necessary to have thorough familiarity with all of these specifications in order to build
a SWORD client for the DANS EASY SWORD v2.0 Service.   

[SWORD website]: http://swordapp.org/about/
[specifications of SWORD v2.0]: http://swordapp.github.io/SWORDv2-Profile/SWORDProfile.html 
[Atom]: https://tools.ietf.org/html/rfc4287
[AtomPub]: https://tools.ietf.org/html/rfc5023
[HTTP]: https://tools.ietf.org/html/rfc2616

### The EASY SWORD v2.0 Implementation

The DANS SWORD v2.0 service uses our own implementation of the protocol. It is developed as open source software on GitHub.
The [easy-sword2] project is intended as a generic component that may be used by other parties that need to host a deposit 
service. For the purpose of client development some parts of the `easy-sword2` documentation are required reading, especially
[the section about its external interface].

[easy-sword2]: https://github.com/DANS-KNAW/easy-sword2
[the section about its external interface]: https://github.com/DANS-KNAW/easy-sword2#sword-interface

EASY Ingest Flow
----------------
After your deposit has been successfully submitted, it enters the EASY Ingest Flow. For the package to be converted
into an archived dataset in EASY it must meet some additional requirements. These requirements are described in the
[DANS BagIt Profile].

[DANS BagIt Profile]: https://doi.org/10.17026/dans-z52-ybfe
  


