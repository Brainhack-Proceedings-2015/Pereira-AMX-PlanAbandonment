---
event: '2015 Brainhack Americas (MX)'

title:  'Detecting task-based fMRI compliance using plan abandonment techniques'

author:

- initials: RFP
  surname: Fraga Pereira
  firstname: Ramon
  email: ramon.pereira@acad.pucrs.br
  affiliation: pucrs

- initials: ASH
  surname: Heinsfeld
  firstname: Anibal Sólon
  email: anibalsolon@gmail.com
  affiliation: pucrs

- initials: ARF
  surname: Rosa Franco
  firstname: Alexandre
  email: alexandre.franco@pucrs.br
  affiliation: pucrs

- initials: AB
  surname: Buchweitz
  firstname: Augusto
  email: augusto.buchweitz@pucrs.br
  affiliation: pucrs

- initials: FM
  surname: Meneguzzi
  firstname: Felipe
  email: felipe.meneguzzi@pucrs.br
  affiliation: pucrs

affiliations:

- id: pucrs
  orgname: 'PUCRS'
  street: Av. Ipiranga, 6681
  postcode: 90619-900
  city: Porto Alegre
  state: Rio Grande do Sul
  country: Brazil

url: https://github.com/brainhack-poa/fmri-plan-recongnition

coi: None

acknow: The authors would like to thank the organizers and attendees of Brainhack MX and the developers of AFNI.

contrib: RFP and FM develop the project, and RFP, ASH, FM, ARF, and AB wrote the report.

bibliography: brainhack-report

gigascience-ref: REFXXX
...

#Introduction
Task-based fMRI is a powerful approach to understand brain processes for a certain task.
However, fMRI images are usually preprocessed hours, days or even months after the scan.
During the functional image preprocessing stage, defects in images are detected and, in some cases, cannot be corrected.
For example, technical problems with the scanner or lack of collaboration from the subject to perform the given tasks.
For these cases it is necessary to realize a new scan.
In order to mitigate lost scans due to patient non-compliance, we need an approach to detect such non-compliance during the scan.

#Approach
In this BrainHack project, we aim to detect if a subject is following the given task and provide an almost real-time feedback to the researchers to make a decision during the exam if the subject is not collaborating.
This is necessary to be performed in order to avoid loss of data, in which the images are typically processed and quality assessed at another day.
We will focus on task where there are no button responses from the subject, hence relying solely in the BOLD signal if the subject is collaborating.
To do so, we use plan abandonment techniques \cite{Sukthankar2014}, a sub-area of Artificial Intelligence.
For a given fMRI paradigm, a plan should be created and compared with the subject's brain activation during the scan using recognition methods.
To use plan abandonment techniques, we need to discretize and formalize the fMRI and construct a expected plan based on the hypothesized paradigm using this formalization.
To evaluate the compliance with a specific paradigm, we aim to use real-time fMRI methods to retrieve BOLD signals of brain regions that are supposed to be active in a particular time range.
In order to tolerate fluctuations of the BOLD signal, we aim to use the methods that detect non-compliance using a threshold from the expected activation \cite[Chap 4]{Sukthankar2014}.
By doing so, it is possible to detect if a subject is following the paradigm given a specific stimulus type, such as visual or auditory stimulus.
The brain state of each stimulus type will be mapped based on atlas from the literature.
For example, to cover motor activations, Brodmann area 4 will be mapped with a state *motor_actv*.
Thus, for a paradigm that works with motor tasks, the plan must contain *motor_actv* for the given time that the task occurs.

#Discussion
The formalization of brain states strongly depends on the discretization of specific region states, which might vary from subject to subject.
In order to normalize the signals, a previous tuning phase is required with simple paradigms, depending on which paradigm will be executed.
During the scan, an online normalization must be made to a standard space, such as the MNI brain space.
This real-time processing is required to map expected active regions to the previously selected brain areas from an atlas.

The usage of real-time fMRI methods aggregates to our approach since the tuning and pursuance recognition can be made during the exam.
Such real-time fMRI methods can also monitor movements during the scan in order to identify if there is too much subject movement.
In the case of fMRI paradigm abandonment, the paradigm can be adapted to induce or interest the subject in a way that the subject proceeds with its tasks, using methods such as demonstrated by \cite{Dongha2011}.
Neurofeedback can be used to sustain the subject's interest by letting the paradigm be more challenging, requiring more attention and collaboration from the patient, such as the paradigm from \cite{deBettencourt2015}.

#Conclusions
This project is in its initial phase.
Real-time fMRI methods are being tested, using AFNI's provided tools.
In order to use plan abandonment techniques, the next step is to formalize basic stimuli types based on mapped regions.
By using these formalizations, paradigms can be converted to a problem of plan abandonment and it becomes possible to evaluate the participation of a subject during the scan.