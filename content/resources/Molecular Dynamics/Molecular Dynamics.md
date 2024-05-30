The basics of molecular dynamics starts from a simple fact from thermodynamics: the **most probable thermodynamic state** is the state which has the **lowest thermodynamic free energy**. Thus, the goal of molecular dynamics is to study the statistical properties of possible molecular configurations, which is completely described by the **[[Partition Function|Partition Function]]**.  

The molecular structure with the lowest free energy is determined by the forces acting on the molecule. Generally, there are 4 forces – bond forces , electrostatic forces, Van der Waals forces, and [[Solvent Interactions|solvent interactions]] (e.g. hydrophobic interactions). However, a computer cannot perfectly represent all 4 forces. Therefore, some assumptions about the force field are necessary (e.g. ignoring the flexibility of water molecules, or ignoring [[Quantum Effects|quantum effects]]). 

Depending on the type of assumptions, there are multiple force field approximations, such as CHARMM, AMBER, or GROMACS. However, there are some common features. Generally, the force field is taken as the negative gradient of the potential, that is $$F = m \dfrac{\mathrm{d^2}r}{\mathrm{d}t^2} = - \nabla V \tag{1}$$ This differential equation is solved by means of time-integration, where time is divided into discrete steps with a order of approximately 1 femto-second. 

The time-evolution of the $N$ atoms in 3D space can be completely represented by means of its trajectory in $6N$ phase-space ($3N$ for position and $3N$ for momenta). However, for the end-goal of molecular dynamics (that is, to generate the partition function), the phase-space trajectory is irrelevant. Only the time-average is relevant (which, by the ergodic hypothesis, is equal to the micro-state average). 

Meanwhile, $V$ itself can be represented as 

$$\begin{align} V_{\text{tot}} &= V_{\text{bonded}} + V_{\text{non-bonded}} \\&= V_{\text{bond}} + V_{\text{angle}} + V_{\text{dihedral}} + \mathcal{o}(\cdots) \\&+ V_{\text{electrostatic}} + V_{\text{Van der waals}} \end{align}$$
This can be calculated as

![[../../../Media/69f5b5b7-cccd-40fb-8a45-0ea46ae78c0d_3350x966.jpg]]

