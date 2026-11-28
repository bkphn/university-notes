[]

$\mathbf{x}=\begin{bmatrix}x^{(t)} \\ x^{(t-1)} \\ x^{(t-2)} \\ x^{(t-3)} \\ x^{(t-4)} \end{bmatrix}$


## Feedforward

Conv Layer:

$$\mathbf{z}^{(t)}=\mathbf{x}\ast\mathbf{w}=\mathrm{ReLU}\begin{bmatrix} 
x^{(t)}w_{1}+x^{(t-1)}w_{2}+x^{(t-2)}w_{3} \\
x^{(t-1)}w_{1}+x^{(t-2)}w_{2}+x^{(t-3)}w_{3} \\
x^{(t-2)}w_{1}+x^{(t-3)}w_{2}+x^{(t-4)}w_{3} \\
\end{bmatrix}$$
Rec Layer

$$\mathbf{h}^{(t)}=\Psi(\mathbf{z}^{(t)}\mathbf{v}_{1}+\mathbf{h}^{(t-1)}\mathbf{v}_{r})$$

$$\mathbf{h}^{(t-1)}=\Psi(\mathbf{z}^{(t-1)}\mathbf{v}_{1}+\mathbf{h}^{(t-2)}\mathbf{v}_{r})$$

$$\mathbf{h}^{(t-2)}=\Psi(\mathbf{z}^{(t-2)}\mathbf{v}_{1}+\mathbf{h}^{(t-3)}\mathbf{v}_{r})$$

Output Layer

$$\hat{y}^{(t)}=\Phi(\mathbf{h}^{(t)}\mathbf{u}_{1}+\mathbf{z}^{(t)}\mathbf{u}_{2}+b)$$
 qws