A completely isolated system, such as the [[Microcanonical Ensemble]] is unrealistic. Therefore, we often imagine a system in constant thermal equillibrium with a reservoir whose temperature is kept constant. Thus, for this system $N$, $V$ and $T$ is constant. The system and its reservoir together constitute the universe, i.e. and isolated system. Based on our previous result, we may thus state that the likelihood of a micro-state $\Gamma$ is in fact
$$\begin{align} \mathbb{P}(\Gamma) &\propto \dfrac{1}{\Omega(E_{\text{univ} } - \mathcal{H}(\Gamma))} \\&= \exp\left(-\dfrac{S(E_{\text{univ}} - \mathcal{H}(T))}{k_B}\right) \\&\propto \exp\left(-\dfrac{\mathcal{H}}{k_BT}\right) = \exp(-\beta \mathcal{H})\end{align}$$
As $\Delta S = \dfrac{\Delta Q}{T}$ with $T$ constant. 

The partition function refers to the function we must multiply to normalize $\mathbb{P}$ which is 
$$\begin{align}Z &= \sum_{\Gamma} \exp(-\beta\mathcal{H}) \tag{Discrete Case}\\&= \dfrac{1}{h^{3N}} \int \mathrm{d}^{6N}\Gamma \exp(-\beta\mathcal{H})  \tag{Continuous Case}\end{align}$$
Note that for the discrete case
$$\begin{align} Z &= \sum_{E} \Omega(E, V, N)\exp(-\beta E) \\&= \sum_{E} \exp\left(-\beta(E-TS^{\text{mc}})\right) \\&= \sum_{E} \exp(-\beta F)\end{align}$$
Where $F$ is the Legendre transform of $U$ (the internal energy) with regard to $T$, otherwise known as the **Helmholtz Free Energy**. Thus implying that
$$F = - k_{B}T \ln Z \tag{1}$$
An alternative method to prove $\text{(1)}$ is through a differential equation. Let $\overline{F} = -k_B T \ln Z$. Note that  $$\begin{align} U =  \left< \mathcal{H} \right> &= \sum_{\Gamma} \mathcal{H} (\Gamma) \times \mathbb{P}(\Gamma) \\&= \dfrac{1}{Z} \sum_{\Gamma} \mathcal{H} \exp\left(-\beta\mathcal{H}\right) \\&= \dfrac{1}{Z} \left(-\dfrac{\partial}{\partial\beta}\right)Z \\&= -\dfrac{\partial}{\partial\beta} \ln Z \end{align} $$We have that 
$$\begin{align} -\dfrac{\partial \overline{F}}{\partial T} &= \dfrac{\partial \beta}{\partial T} \dfrac{\partial}{\partial \beta} \left(k_BT\ln Z\right) \\&= -k_B\beta^2 \dfrac{\partial}{\partial \beta} \left(\dfrac{\ln Z}{\beta}\right) \\&= k_B \ln Z + k_B\beta U \\&= \dfrac{-\overline{F} + U}{T} \end{align}$$
Also note that 

$$-\dfrac{\partial F}{\partial T} = S = \dfrac{-F + U}{T}$$
thus $F$ and $\overline{F}$ obey exactly the same first-order differential equation. 

Meanwhile, at $T \rightarrow 0+$, $Z$ is dominated by the term $\exp\left(-\beta E_{0}\right)$ , thus $\overline{F}$ tends toward $E_0$. Meanwhile, $F = U - TS$ also tends toward $E_0$ at $T=0$. Thus, $F$ and $\overline{F}$ obey the same first-order differential equation and have the same initial value, thus completing our proof. 