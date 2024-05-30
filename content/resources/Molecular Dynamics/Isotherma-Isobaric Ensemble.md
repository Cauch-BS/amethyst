*Symbols*: $Z$ denotes the partition function for the canonical ensemble, $\mathbf{Z}$ for the isotherma-isobaric ensemble, and $\mathcal{Z}$ for the grand canonical ensemble. 
 
 In the isotherma-isobaric ensemble the volume of the system is not fixed. Thus the system is also in pressure equillibrium as well a thermal one. ($N$, $P$ and $T$ are fixed) 

$$\begin{align} \mathbb{P}(\Gamma) &\propto \dfrac{1}{\Omega(E_{\text{univ} } - \mathcal{H}(\Gamma), V- V(\Gamma))} \\&= \exp\left(-\dfrac{S(E_{\text{univ}} - \mathcal{H}(T), V-V(\Gamma))}{k_B}\right) \\&\propto \exp\left(-\dfrac{\mathcal{H(\Gamma)} + PV(\Gamma)}{k_BT}\right) = \exp(-\beta (\mathcal{H(\Gamma)} + PV(\Gamma)) )\end{align}$$
With the partition function being given by 
$$\mathbf{Z} = \int_{0}^{\infty} \dfrac{\mathrm{d}V}{h^{3N}} \int d^{6N} \Gamma \exp(-\beta \mathcal{H}-\beta P V)$$
for the continuous case, or alternatively 
$$ \mathbf{Z} = \sum_{\Gamma} \exp(-\beta(\mathcal{H}(\Gamma) + PV(\Gamma))$$
 Note that for the discrete case
 $$\begin{align} \mathbf{Z} &= \sum_{E,V} \Omega(E, V, N)\exp(-\beta E - \beta PV) \\&= \sum_{E, V} \exp\left(-\beta(E-TS^{\text{mc}} + PV)\right) \\&= \sum_{E} \exp(-\beta G)\end{align}$$
Where $G$ is the **Gibbs Free Energy**. Similar to before, this leads us to conclude that $G = -k_BT \ln \mathbf{Z}$. 
