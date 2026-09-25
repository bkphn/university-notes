## Kostki
**Kostką** $Q_k$ nazywamy graf, którego zbiorem wierzchołków jest zbiór wszystkich ciągów binarnych długości $k$:

$$V(Q_k )=\mathbb{Z}_{2}^k$$

natomiast dwa ciągi połączone są krawędzią wtedy, gdy różnią się na dokładnie jednej współrzędnej.

Dla każdego $k$ zachodzi:

$$|V(Q_k )|=2^k,  \qquad |E(Q_k )|=k\cdot 2^{k−1}$$

## Cykle w grafach
Rozmiar najkrótszego cyklu w grafie $G$ nazywamy jego **talią**. Rozmiar najdłuższego cyklu w grafie $G$ nazywamy jego **obwodem**.

## Graf trójdzielny
Niech $p,q,r\in \mathbb{N}_{+}$, graf pełny trójdzielny $K_{p,q,r}$ to graf, w którym zbiór wierzchołków można rozdzielić na trzy parami rozłączne zbiory:

$$V(K_{p,q,r})=V_1\cup V_2\cup V_3$$

i w którym dwa wierzchołki są połączone wtedy i tylko wtedy, gdy nie należą do tego samego zbioru $V_i$.

## Graf $n$-dzielny:
Niech $m_i\in \mathbb{N}_{+}$, a $i\in \{1, \dots,n\}$. Grafem $n$-dzielnym nazywamy graf $K_{m_1,m_2,\dots,m_n}$, w którym zbiór wierzchołków można rozdzielić na rozłączne zbiory:

$$V(K_{m_1,m_2,\dots,m_n})=\bigcup_{i=1}^n V_{i}$$

w którym dwa wierzchołki są połączone wtedy i tylko wtedy, gdy nie należą do tego samego zbioru $V_{i}$.
