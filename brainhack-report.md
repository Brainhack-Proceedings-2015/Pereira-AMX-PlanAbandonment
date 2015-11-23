---
event: '2015 Brainhack Americas (MX)'

title:  'Detecting task-based fMRI pursuance using plan abandonment approaches'

author:

- initials: RFP
  surname: Fraga Pereira
  firstname: Ramon
  email: anibalsolon@gmail.com
  affiliation: pucrs

- initials: ASH
  surname: Heinsfeld
  firstname: Anibal Sólon
  email: anibalsolon@gmail.com
  affiliation: pucrs

- initials: FM
  surname: Meneguzzi
  firstname: Felipe
  email: felipe.meneguzzi@pucrs.br
  affiliation: pucrs

affiliations:

- id: pucrs
  orgname: 'Pontifical Catholic University of Rio Grande do Sul'
  street: Av. Ipiranga, 6681
  postcode: 90619-900
  city: Porto Alegre
  state: Rio Grande do Sul
  country: Brazil

url: https://github.com/brainhack-poa/fmri-plan-recongnition

coi: None

acknow: The authors would like to thank the organizers and attendees of Brainhack MX and the developers of AFNI.

contrib: RFP and FM develop the project, and RFP, ASH and FM wrote the report.

bibliography: brainhack-report

gigascience-ref: REFXXX
...

#Introduction
Task-based fMRI is an interesting approach for understand brain processes for a given task.
However, fMRI images are usually preprocessed hours, or even days, after the scan.
During preprocssing stage, defects in images are detected and, in some cases, can not be corrected.
For example, technical problems or lack of collaboration from the subject to realize the given tasks.
For this cases, it is necessary to realize a new scan.

#Approach
In this BrainHack project, we aim to detect if the subject is following the given task and give an almost real-time feedback to the researchers make decisions (e.g. restart the task), in order to avoid images discard or rescans.
To do so, we use Automated Planning techniques \cite{Sukthankar2014}, an sub-area of Artificial Intelligence.
For a given fMRI paradigm, a plan should be created and compared with the subject's brain activations during scan using recognition methods.
In order to use plan recognition methods, we need to discretize and formalize the fMRI, and construct a expected plan based on the hypothesis paradigm using this formalization.
To evaluate the pursuance of a specific paradigm, we aim to use real-time fMRI method to retrieve BOLD signals of brain regions that are supposed to be active in a particular time range.
By doing so, it is possible to detect if a subject is following the paradigm given a specific stimulus type, such as visual or auditory stimulus.
The brain state of each stimulus type will be mapped based on atlas literature.
For example, Brodmann areas 17, 18 and 19 will be mapped to cover visual stimilus with a state *visual_actv*.
So, for a paradigm that works with visual stimuli, the plan must contain *visual_actv* for the given time that the stimulus occurs.

#Discussion
The formalization of brain states highly depends on the discretization of specific region states, that might vary for each subject.
In order to normalize the signals, a previous tunning phase is required with simple paradigms, depending of which paradigm will be executed.
The usage of real-time fMRI methods aggregates to our approach, since the tunning and pursuance recognition can be made during the exam.
In case of fMRI paradigm abandonment, the paradigm can be adapted to induce or interest the subject in a way that the subject proceed with its tasks, using methods such as demonstred by \cite{Dongha2011}.

#Conclusions
This project is in its initial phase.
Real-time fMRI methods are being tested, using AFNI's provided tools.
The next step is to formalize basic stimuli types based on mapped regions.
Using these formalizations, paradigms can be converted to plans and it become possible to evaluate the participation of a subject during the scan.