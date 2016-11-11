DANS EASY Services
==================
Welcome to the DANS EASY Services web page! DANS offers, through its Electronic Archiving SYstem (EASY), long-term
data preservation services to the scientific research community. Please, refer to the [DANS website] for more general
information about our organisation, services and activities.

[DANS website]: https://www.dans.knaw.nl/en

What is EASY?
-------------
EASY is the DANS long-term preservation archive for the scientific research data. It is a Trusted Digital Repository
with the [Data Seal of Approval (DSA)] and the [Nestor Seal]. It offers several deposit interfaces (see next section), 
identifier services and a search interface.

[Data Seal of Approval (DSA)]: http://www.datasealofapproval.org/en/
[Nestor Seal]: http://www.langzeitarchivierung.de/Subsites/nestor/EN/nestor-Siegel/siegel_node.html

Deposit Interfaces
------------------
EASY offers two interfaces for depositing data: a web form, intended for direct user access, and a machine-machine
interface that allows partner organisations of DANS to automatically deposit data packages from their front-end archives
into EASY. The machine-machine interface implements the [SWORD-protocol].

[SWORD-protocol]: http://swordapp.org/

### Web Form
Users of EASY can directly access the [web form] to deposit their data in EASY. Data that is deposited in this way is 
checked for preservability and intelligibility by our data managers before publication. The depositor is responsible for
uploading their dataset according to certain guidelines. See the [deposit guide] for more details. ([A version in Dutch] is also available.)

[web form]: https://easy.dans.knaw.nl/ui/deposit
[deposit guide]: pdf/DEP_All%20other%20disciplinesUK.pdf
[A version in Dutch]: pdf/DEP_All%20other%20disciplinesNL.pdf

### Machine-machine Interface (SWORD)
Partner organisations of DANS can connect their repository systems to EASY, so that they can send copies of their data packages to
EASY for long term preservation, automatically. The copy can either be a regular EASY dataset that can be downloaded through the
EASY Web-UI or a "dark archive" copy, which is findable through the EASY search interface, but will redirect the user to the 
front-end archive for access to the data (i.e. the data will *not* be accessible through EASY).

There are currently two versions of SWORD operational:

* **SWORD v1.3** - an older version of the SWORD protocol. It supports creating regular EASY datasets that are accessible and downloadable
  through the Web-UI. See the *["SWORD Auto-Ingest Manual"]* for technical details.
* **SWORD v2.0** - the latest version of the SWORD protocol. The EASY implementation currently only supports creating dark archive datasets,
  though work is underway to make depositing downloadable datasets possible. See the page *["Depositing in EASY with SWORD 2.0"]* for technical details.
  
#### How to connect your Repository System to EASY?
If you are interested in using EASY as your back-end Trusted Digital Repository (TDR), please contact DANS at: info@dans.knaw.nl.
Our SWORD account manager will then work with you to draw up the necessary agreements and guide you through the steps to making the 
tranfer system operational.


["SWORD Auto-Ingest Manual"]: pdf/SWORD%20Auto-Ingest%20Manual.pdf
["Depositing in EASY with SWORD 2.0"]: sword2.html










