## Neuron rekurencyjny
$x_{1},x_{2} \rightarrow h$

$h$ zamiast $y$ w sieciach rekurencyjnych.
$rekurencja \Delta  h^{(t-1)}$
Waga $w_{r}$

Szereg czasiowy
$h^{(t)}$ ↑ 
    → $t$

## Inference

$$h^{(t)}=\Psi(w_{1}x_{1}^{(t)}+w_{2}x_{2}^{(t)}+w_{r}h^{(t-1)})$$


Nie możemy używać BP bo pochodne są same w sobie i wpadamy w pętlę, dlatego robimy BPTT, czyli traktujemy konkretne $h^{(i)}$ jako różne zmienne.

Zaczynamy od unfoldingu. Czyli usuwamy $\Delta$ i traktujemy jako osobne neurony Możemy unfoldować ile razy chcemy. Zazwyczaj unfoldujemy setki razy. Jeżeli potrafimy możemy unfodlować aż do początku, ale zazwyczaj jest to niemożliwe i wtedy ostatni unfold przyjmujemy sami.



$$\mathcal{L}=\frac{1}{T}\sum_{t=1}^T (y^{(t)}-h^{(t)})^2$$

$w_{1}\leftarrow w_{1}-\eta \frac{\partial\mathcal{L}}{\partial w_{1}}$

$$\frac{\partial\mathcal{L}}{\partial w_{1}} = \frac{∂\mathcal{L}}{\partial h^{(t)}}\left( \frac{\partial h^{(t)}}{\partial w_{1}}+\frac{\partial h^{(t)}}{\partial h^{(t-1)}}\left( \frac{\partial h^{(t-1)}}{\partial w_{1}} + \frac{\partial h^{(t-1)}}{\partial h^{(t-2)}}  \cdot \frac{\partial h^{(t-2)}}{\partial w_{1}}\right)  \right)$$

$\frac{\partial\mathcal{L}}{\partial h^{(t)}} = \frac{2}{T} \sum_{t=1}^T (y^{(t)}-h^{(t)})(-1)$

$\frac{\partial h^{(t)}}{\partial w_{1}}=\Psi'(w_{1}x_{1}^{(t)}+w_{2}x_{2}^{(t)}+w_{r}h^{(t-1)})x^{(t)}=\Psi'(\cdot)\Big|_{t}\cdot x^{(t)}$

$\frac{\partial h^{(t)}}{\partial h^{(t-1)}}=\Psi'(w_{1}x_{1}^{(t)}+w_{2}x_{2}^{(t)}+w_{r}h^{(t-1)})\cdot w_{r}=\Psi'(\cdot)\Big|_{t}\cdot w_{r}$

$\frac{\partial h^{(t-1)}}{\partial w_{1}}=\Psi'(\cdot)\Big|_{t}\cdot x^{(t-1)}$

$\frac{\partial h^{(t-1)}}{\partial h^{(t-2)}}=\Psi'(\cdot)\Big|_{t-1}\cdot w_{r}$

$\frac{\partial h^{(t-2)}}{\partial w_{1}}=\Psi'(\cdot)\Big|_{t-2} x_{1}^{(t-2)}$


będzie na argzaminie

$w_{r}$ się dużo razy powtarza i pojawia się w każdym rozwinięciu, przy $N$ unfoldingach otrzymujemy $w_{r}^{N}$, jeżeli $w_{r}$ jest mniejsze od 1 i większe od -1, wtedy w_r→0 to dochodzi do gradient vanishing, a jeżeli jest większe to dochodzi do gradient exploding i w_r → ∞.

spiking neural netowrk
s


$$\frac{\partial{ \mathcal{L} }}{\partial{ w_{r}  }}=\frac{\partial{ \mathcal{L} }}{\partial{ h^{(t)} }}\left( \frac{\partial{ h^{(t)} }}{\partial{  w_{r} }}  +\frac{\partial{ h^{(t)} }}{\partial{  h^{(t-1)} }} \left( {\frac{\partial{ h^{(t-1)} }}{\partial{ w_{r}  }}} + \frac{\partial{ h^{(t-1)} }}{\partial{ h^{(t-2)}  }} \left( {\frac{\partial{ h^{(t-2)} }}{\partial{ w_{r} }}} \right) \right)\right)$$

$\frac{\partial{ \mathcal{L} }}{\partial{ h^{(t)}  }}=\frac{1}{T} \sum_{t=1}^T (y^{(t)}-h^{(t)})^2(-1)$

$\frac{\partial{ \mathcal{h^{(t)}} }}{\partial{ w_{r} }}=\Psi'(w_{1}x_{1}^{(t)}+w_{2}x_{2}^{(t)}+w_{r}h^{(t-1)})\cdot h^{(t-2)}$

$\frac{\partial{ h^{(t)} }}{\partial{  h^{(t-1)} }}=\Psi'(w_{1}x_{1}^{(t)}+w_{2}x_{2}^{(t)}+w_{r}h^{(t-1)})\cdot w_{r}$

$\frac{\partial{ h^{(t-1)} }}{\partial{ w_{r}  }}=\Psi'(w_{1}x_{1}^{(t-1)}+w_{2}x_{2}^{(t-2)}+w_{r}h^{(t-2)})\cdot h^{(t-2)}$

$\frac{\partial{ h^{(t-1)} }}{\partial{ h^{(t-2)}  }}=\Psi'(w_{1}x_{1}^{(t-1)}+w_{2}x_{2}^{(t-1)}+w_{r}h^{(t-2)})\cdot w_{r}$

$\frac{\partial{ h^{(t-2)} }}{\partial{  w_{r} }}=\Psi'(w_{1}x_{1}^{(t-2)}+w_{2}x_{2}^{(t-2)}+w_{r}h^{(t-3)})\cdot h^{(t-3)}$
