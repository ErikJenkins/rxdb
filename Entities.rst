Entities and Relationships
==========================

Motivation
----------

The foundation of a well-run pharmacy is a set of complete and accurate
records. Granted, a good bit of the information will just sit there
never to be referenced again -- and that's a good thing. Because most of
those little details are only needed  when there is a problem. And then,
little things like product lot numbers and specific dates and times can
become absolutely vital.

The purpose of this document is to lay out the entities a pharmacy
software system needs to track and how they relate to one another. I.e.
to form the basis of a relational database schema.

Overview
--------

A *patient* has some number of *prescriptions*. Each prescription
belongs to a specific patient. A *prescriber* meets with a patient at a
specific location or *clinic*. A given prescriber is not limited to one
clinic and a clinic may host multiple prescribers. A prescription
identifies the patient for which it was written, the authorizing
prescriber, the clinic where the prescriber met with the patient, and
the *medication* to be dispensed. The indicated medication may be
dispensed on one or more occasions known informally as *fills*.

A medication consists of one or more *drugs*. A given medication may be
available as one or more commercial *products*. If not available
commercially, a compounded product may need to be made in order to
fulfil a prescription. A product may be supplied in a variety of
*packages*.

Patient
-------

When someone walks in to a pharmacy for the first time, a profile needs
to be set up for them before anything else can happen. The pharmacy
staff needs to be able to identify the patient to ensure that the
correct prescriptions go to the appropriate patients. Contact
information is needed in case there are any problems. Any information
that may impact the health of the patient or which medications may be
most appropriate in a given situation must also be recorded.

Identity
````````

This is about making sure that the right medications go the the right
person. At a minumum this usually means the patient's name, gender, and
date of birth. Other means of identification may be necessary,
particularly for patients who receive controlled substances. 

Given names can be tricky as one person may answer to more than one
name. A patient may give his name as "William" when dropping off his
first prescription, while his wife may ask to pick up refills for "Bill"
a month later. Family names tend to be consistent and should thus be
given more weight when seeking a match. Different ideas about proper
spelling and pronunciation can also cause difficulties.

The date of birth is helpful in resolving confusion over patient names
such as those described above.

Contact
```````

There are a number of situations that would require the pharmacy to get
in touch with a patient urgently. The patient's address and phone number
are the minumum. This can be problematic when the pharmacy serves
homeless patients, but every effort should be made record whatever
information would be necessary to locate a patient.

There are a number of means of communicating: landlines, cell phones,
email, SMS, etc. A flexible means of recording existing and future forms
of address is essential.

Health Information
``````````````````

Any information that may affect the safety and/or effectiveness of a
potential medication needs to be noted in the patient's profile.
Standard categories include: drug allergies, adverse reactions to drugs
previously taken, and history of chronic illnesses. Plus anything else
the pharmacy staff needs to note about the patient. [#]_

.. [#] Knowing the time and date when notes are made can indicate which
    supercedes the other in cases of conflicting information.

Prescriber
----------

Prescriptions must be authorized by someone with the appropriate
authority. The name of prescriber and any identifiers or certifications
that establish that his or her right to issue prescriptions should be
recorded. Physicians, (doctors of medicine and osteology in the U.S.,)
have general prescribing authority for human patients. Other health
professions have prescribing ability limited by their scope of practice
or by supervision from another prescriber. Supervised, (known as
mid-level,) prescribers work under another prescriber of greater
expertise or experience who should be identified in their records.

Clinic
------

Generally speaking, a prescriber will issue a prescription after
examining a patient in person. This meeting will occur at a specific
location sometimes known as a "practice site". This document will use
the term clinic to refer to this location. A prescriber may practice in
more than one clinic and multiple prescribers may be seeing patients at
a single clinic. A specific prescription will be associated with a
specific clinic and, importantly, that clinic will hold any relevant
medical records.

The phone number listed on the prescription may or may not be
exclusively for the prescriber, but should allow one to contact the
prescriber or an agent of the prescriber. [#]_

.. [#] The phone number may be a general number for the clinic, it may
    may be specific to that prescriber, or it may be for a subset of
    prescribers at that clinic.

Prescription
------------

Besides connecting patient, prescriber, clinic, and medication, a
prescription records the date it was written, the number of refills
authorized, the quantity of the medication authorized, and instructions.

Fill
````

A fill records the date, the specific product used, and the quantity
provided to the patient. Information from the product packaging must
also be noted so that what the patient recieves can be traced to a
specific time and place of manufacture and vice versa. This way any
problems due to the manufacturing process can be traced and other
patients warned.

Medication
----------

A medication consists of one or more *drugs*. Each drug indicated has an
associated strength or concentration. A medication can be specified by
listing the drugs by generic names or by indicating the brand name of a
product. If a brand name is used then, depending on the circumstances,
the pharmacy may be obliged to dispense the specific product named.
Otherwise an equivalent product containing the same drug or drugs as the
branded product may be substituted.

Drug
----

A drug is a specific chemical compound used in the treatment of disease.
Drugs are identified by *generic* names. Drugs are classified with
regard to how they are restricted. The classification should be marked
to remind staff of the appropriate handling.

Some drugs can be sold without a prescription and are called *over the
counter* drugs or *OTCs* for short, Although they can be purchased
without a prescription, they are sometimes prescribed. 

More strictly regulated are prescription only drugs, known in the U.S.
as *legend* drugs. Improper use can cause serious harm, so expert
oversight is necessary.

Finally there are drugs that are commonly, and intensionaly, abused. In
the U.S. these are called *controlled substances* and are grouped into
schedules identified by roman numerals. Schedule I being the most
restricted, (these should never be prescribed.) And schedule V being the
least restricted. (In the U.K. they group them into classes identified
by letters. E.g. U.K. class A is roughly equivalent to the U.S. schedule
I.)

Product
-------

A product contains one or more drugs. Some products are sold under a
*brand* name while others are labelled with the generic names of the
drugs contained. A newly approved drug under patent protection will only
be available in branded products. The first product in which a new drug
is sold is known as the *innovator* product. 

After patent protection expires on the drug, other manufacturers are
free to use the drug in new products. Even so, the innovator product is
still considered the standard for comparison. In the U.S. the Food and
Drug Administration publishes comparison data, (in the *Orange Book*,)
and only products that are known to be equivalent to the innovator
should be substituted for it.

N.B. brands refer to products, not drugs. While it does not happen very
often, a branded product can reformulate and start using a different
drug.

Package
-------

Products come in one or more packages. A bottle of 100 tablets is
considered a distinct package from a bottle of 500. The physical package
also bears the expiration date and lot number. The expiration date
indicates the latest date at which the drug should be considered to have
full potency. The lot number is a code used to trace the package to the
time and place the product was made. If there are any problems found
this can be used to see whom else may be effected.

.. vim: ai tw=72
