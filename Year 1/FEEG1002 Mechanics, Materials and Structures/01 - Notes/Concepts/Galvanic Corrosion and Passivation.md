---
title: "Galvanic Corrosion and Passivation"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part C: Materials"
aliases: ["corrosion", "galvanic corrosion", "standard emf series", "electrode potential", "cell voltage", "galvanic series", "passivation", "sacrificial anode", "cathodic protection", "impressed current"]
tags: [feeg1002, concept, materials, corrosion]
status: complete
date: 2026-11-05
parent_lectures: ["[[FEEG1002 C9 - Fatigue, Creep and Corrosion]]"]
related_concepts: ["[[Nernst Equation and Galvanic Series]]", "[[Iron-Carbon Phase Diagram]]"]
sources: ["02 - Sources/Materials/Lectures/Lecture 15 - Failure of Materials 4 - Creep and Corrosion.pdf"]
---

# Galvanic Corrosion and Passivation

Galvanic corrosion is the electrochemical attack of the more anodic of two electrically connected metals in an electrolyte; passivation is the protection some metals get from a thin, adherent oxide film that stifles further attack.

Wet corrosion needs two coupled reactions. At the anode the metal is oxidised and goes into solution, $\mathrm M\rightarrow\mathrm M^{n+}+ne^-$; at the cathode the electrons are used up by a reduction, such as $2\mathrm H^++2e^-\rightarrow\mathrm H_2$ in an acid. The rates must balance, and it is the anode that corrodes. Which metal of a pair is the anode is set by the standard electrode potentials, measured against the hydrogen electrode: the more negative metal is the anode, and the cell voltage is

$$
E_{cell}=E_{cathode}-E_{anode}
$$

so iron coupled to copper gives $0.340-(-0.440)=0.780$ V, with the iron dissolving. The further apart the two metals, the larger the voltage and the faster the anode corrodes.

![[m9_emf_series.png|900]]

Real alloys in seawater are ranked by the galvanic series instead, because chloride ions change the electrochemistry and oxide films make some metals behave far more nobly than their standard potential suggests. That is passivation: aluminium, chromium and titanium form an adherent, defect-free ceramic oxide that conducts no electrons and blocks the diffusion of ions, so titanium, very negative in the emf series, is almost inert in seawater, and stainless steel has separate active and passive entries.

The same electrochemistry gives the protection methods. A sacrificial anode is a more reactive metal coupled to the structure on purpose, such as zinc on galvanised steel or magnesium on buried pipes; impressed current forces the structure to be the cathode; insulation breaks the circuit between dissimilar metals; coatings keep the electrolyte off. The design rules follow too: avoid small anodes on large cathodes, avoid crevices and water traps where oxygen depletion creates anodes, and isolate dissimilar metals.

## Related

- [[FEEG1002 C9 - Fatigue, Creep and Corrosion#Anodic and cathodic reactions|anodic and cathodic reactions]] · [[FEEG1002 C9 - Fatigue, Creep and Corrosion#The standard emf series and cell voltage|the emf series and cell voltage]] · [[FEEG1002 C9 - Fatigue, Creep and Corrosion#The galvanic series|the galvanic series]] · [[FEEG1002 C9 - Fatigue, Creep and Corrosion#Eight forms of corrosion|eight forms of corrosion]] · [[FEEG1002 C9 - Fatigue, Creep and Corrosion#Passivation|passivation]] · [[FEEG1002 C9 - Fatigue, Creep and Corrosion#Protecting against corrosion|protection]] · [[FEEG1002 C9 - Fatigue, Creep and Corrosion#Designing against corrosion|design rules]] · [[FEEG1002 C9 - Fatigue, Creep and Corrosion#Worked example - which metal corrodes|worked example]]
- [[FEEG1002 Materials Tutorial 4 - Failure of Materials Solutions#Q7 - Corrosion of titanium and protecting buried steel|Tutorial 4, Q7]]
- Year 2: [[Nernst Equation and Galvanic Series]] · [[SESA2028 M3 - Corrosion, Wear and Surface Engineering]]
