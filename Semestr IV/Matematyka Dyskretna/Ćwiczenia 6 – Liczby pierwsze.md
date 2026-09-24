## Twierdzenie o lukach między liczbami pierwszymi
Znane od starożytności twierdzenie o lukach między liczbami pierwszymi mówi, że:

>[!danger] Twierdzenie o lukach między liczbami pierwszymi
> Dla każdej liczby całkowitej dodatniej $n$ istnieje taki ciąg złożony z $n$ kolejnych liczb całkowitych, że każdy jego element jest liczbą złożoną.

Fakt ten możemy łatwo udowodnić korzystając z własności silni. Niech $n\in\mathbb{N}$. Możemy zauważyć, że liczba $(n+1)!$ jest podzielna przez każdą z liczb $d\in\{2, 3, 4, 5, \cdots,n−1,n, n+1\}$. Możemy skonstruować ciąg kolejnych liczb: $$(n+1)!+2, \quad (n+1)!+3, \quad\dots,\quad (n+1)!+(n+1)$$
Powyższy ciąg składa się z dokładnie $n$ elementów, przy czym łatwo można zauważyć, że pierwszy element dzieli się przez $2$, ponieważ $2\vert(n+1)!$, oraz $2\vert{2}$, w uogólnieniu każdy $k$-ty element dzieli liczba $k+1$. Jako, że $(n+1)!+(k+1)>k+1>1$, to każdy element tego ciągu jest liczbą złożoną.
## Liczby Mersenne'a
Liczbą Mersenne'a nazywamy liczby w postaci $M_n=2^n−1$, gdzie $n\in\mathbb{N}$. Liczby Mersenne’a zostały tak nazwane na cześć francuskiego matematyka Marina Mersenne’a, który opublikował (błędną) listę liczb pierwszych, będących liczbami Mersenne'a.

Mimo błędów w liście Marina Mersenne'a liczby te są wyjątkowo skutecznym narzędziem poszukiwania liczb pierwszych. Liczby takie nazywamy **liczbami pierwszymi Mersenne'a**. Warunkiem koniecznym aby $M_n$ było liczbą pierwszą jest, aby $n\in\mathbb{P}$, nie jest to jednak warunek wystarczający. Mimo, że $M_2,M_3,M_5$ i $M_7$ są liczbami pierwszymi, to $M_{11}\not\in\mathbb{P}$, ponieważ: $$M_{11}=2^{11}-1=2047=23\cdot 89$$
Od 1997 roku liczby Mersenne'a są wykorzystywane do poszukiwania największych liczb pierwszych, odpowiada za to projekt internetowy GIMPS (*Great Internet Mersenne Prime Search*). W 2025 roku największą znaną liczbą pierwszą jest: $$M_{136279841}=2^{136279841}−1$$
