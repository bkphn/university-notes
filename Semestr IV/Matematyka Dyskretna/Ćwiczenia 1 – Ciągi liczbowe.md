## Pochodna liczby naturalnej
Pochodną liczby naturalnej $n\in\mathbb{N}$ nazywamy liczbę naturalną $n'\in\mathbb{N}$, którą otrzymujemy w następujący sposób: w zapisie binarnym liczby $n$ każdą parę sąsiednich cyfr zastępujemy ich XORem $\oplus$.

> [!example] 
> Przykładowo pochodną liczby $44$ jest $26$, ponieważ:
>
> $$44' = 101100_{(2)}' = \big((1 \oplus 0)\ \ (0 \oplus 1)\ \ (1 \oplus 1)\ \ (1 \oplus 0)\ \ (0 \oplus 0)\big)_{(2)} = 11010_{(2)} = 26$$
>

Dla $n\ge2$ zachodzą własności:

$$(2^n )^′=2^{n−1}$$

$$(2^n−1)^′=0$$

> [!example] Udowodnij własności pochodnej liczby naturalnej
> 
> **1. Pochodna z potęgi liczby 2:**
>
> $$(2^n)' = \left( 1 \underbrace{00\dots0}_{n \text{ razy}} \right)_{(2)}' = \underbrace{(1 \oplus 0)}_{= 1} \underbrace{(0 \oplus 0) \dots (0 \oplus 0)}_{n-1 \text{ razy}} = \left( 1 \underbrace{00\dots0}_{n-1 \text{ razy}} \right)_{(2)} = 2^{n-1}$$
>
> **2. Pochodna z liczby o postaci $2^n - 1$:**
>
> $$(2^n - 1)' = \left( 1 \underbrace{00\dots0}_{n \text{ razy}} - 1 \right)_{(2)}' = \left( \underbrace{11\dots1}_{n \text{ razy}} \right)_{(2)}' = \underbrace{(1 \oplus 1)}_{= 0} \dots \underbrace{(1 \oplus 1)}_{= 0} = 0$$
>

## Uwięziony skoczek
Rozważmy nieskończoną szachownicę, jedno z pól tej szachownicy oznaczmy liczbą $1$, następnie po spirali, w kolejnych polach, umieszczamy kolejne liczby naturalne. Wypełniona szachownica powinna wyglądać następująco:
![[Pasted image 20260904143611.png|231]]

Następnie na polu o numerze $1$ umieszczamy skoczka ♞. Skoczek ten może przemieszczać się zgodnie ze standardowymi zasadami poruszania, przy czym wymagamy, by:
- skoczek nigdy nie znalazł się dwukrotnie na tym samym polu,
- skoczek zawsze poruszał się na pole o najmniejszej dostępnej wartości.

Ciąg utworzony z kolejnych, odwiedzonych przez skoczka liczb nie jest nieskończony, w pewnym momencie kończą się dostępne pola, a skoczek zostaje uwięziony. Otrzymujemy w ten sposób ciąg o dokładnie 2017 elementach:
$1, 10, 3, 6, 9, 4, 7, 2, 5, 8, 11, …, 3101, 2880, 2467, 2084$

Ciąg ten w OEIS (On-line Encyclopedia of Integer Sequences) jest opisany jako ciąg [A316667](https://oeis.org/A316667).

## Spirala Ulama
Spirala Ulama nazywana również spiralą liczb pierwszych to graficzna metoda zaprezentowania rozkładu liczb pierwszych, zaproponowana przez polskiego matematyka Stanisława Ulama w 1963 roku. Zaczynamy od rozpisania spirali na tablicy w sposób identyczny do tej z uwięzionego skoczka.

Następnie zamalowujemy wszystkie liczby pierwsze występujące w spirali. W efekcie na niektórych przekątnych otrzymujemy krzywe linie, wyznaczające pewną regularność występującą w rozkładzie liczb pierwszych. Do dnia dzisiejszego nie odpowiedziano na pytanie, dlaczego liczby pierwsze generują takie a nie inne linie.
![[Pasted image 20260904143717.png|237]]

## Ciąg toczącego Syzyfa
Prowadzący dr Pawlik zadał zadanie zaprezentowania mu skończonego ciągu, który w pewnym momencie samoistnie się kończy. Po paru nocach udało mi się stworzyć autorski ciąg, który nazwałem ciągiem toczącego Syzyfa.

Dana jest oś liczb naturalnych. Umieszczamy Syzyfa $\sigma$ na pozycji startowej $a_{1}=1$. Następnie w każdym kroku obliczamy kolejną pozycje Syzyfa. Jeżeli Syzyf znajduje się obecnie na liczbie $n$ z niedomiarem, bądź doskonałej – czyli takich, których suma dzielników właściwych $s(n)\leq n$, to Syzyf porusza się do góry o dwukrotność liczby jego dzielników $d(n)=|D_{n}|$. W przeciwnym przypadku, czyli gdy $s(n)>n$, kamień okazuje się zbyt ciężki i Syzyf spada o nadmiar liczby, na której stoi $|s(a_{n})-n|$. W ujęciu matematycznym ciąg ten opisujemy takim równaniem:

$$a_{n+1} = \begin{cases}
a_{n}+2\cdot d(n), \quad s(a_{n})\leq a_{n} \\
2\cdot a_{n}-s(a_{n}), \quad s(a_{n})>n
\end{cases}$$

Ciąg kończy się gdy Syzyf spadnie do liczby, na której już stał.

Sumę dzielników właściwych liczby $n$ nazywamy **sumą alikwotową** liczby $n$ i oznaczamy jako:

$$s(n)=\sum_{i\in D_{n}\setminus\set{n}}i$$

Ciąg ten w OEIS (On-line Encyclopedia of Integer Sequences) jest opisany jako [ciąg A394060](https://oeis.org/A394060).

Otrzymany w ten sposób ciąg wpada w pętlę dopiero po 898 elementach. Ciąg prezentuje się następująco:

1, 3, 7, 11, 15, 23, 27, 35, 43, 47, 51, 59, 63, 75, 87, 95, 103, 107, 111, 119, 127, 131, 135, 151, 155, 163, 167, 171, 183, 191, 195, 211, 215, 223, 227, 231, 247, 255, 271, 275, 287, 295, 303, 311, 315, 339, 347, 351, 367, 371, 379, 383, 387, 399, 415, 423, 435, 451, 459, 475, 487, 491, 495, 519, 527, 535, 543, 551, 559, 567, 587, 591, 599, 603, 615, 631, 635, 643, 647, 651, 667, 675, 699, 707, 715, 731, 739, 743, 747, 759, 775, 787, 791, 799, 807, 815, 823, 827, 831, 839, 843, 851, 859, 863, 867, 879, 887, 891, 911, 915, 931, 943, 951, 959, 967, 971, 975, 999, 1015, 1031, 1035, 1059, 1067, 1075, 1087, 1091, 1095, 1111, 1119, 1127, 1139, 1147, 1155, 1187, 1191, 1199, 1207, 1215, 1239, 1255, 1263, 1271, 1279, 1283, 1287, 1311, 1327, 1331, 1339, 1347, 1355, 1363, 1371, 1379, 1387, 1395, 1419, 1435, 1451, 1455, 1471, 1475, 1487, 1491, 1507, 1515, 1531, 1535, 1543, 1547, 1563, 1571, 1575, 1501, 1509, 1517, 1525, 1537, 1545, 1561, 1569, 1577, 1585, 1593, 1609, 1613, 1617, 1641, 1649, 1657, 1661, 1669, 1673, 1681, 1687, 1695, 1711, 1719, 1731, 1739, 1747, 1751, 1759, 1763, 1771, 1787, 1791, 1803, 1811, 1815, 1839, 1847, 1851, 1859, 1871, 1875, 1895, 1903, 1911, 1935, 1959, 1967, 1975, 1987, 1991, 1999, 2003, 2007, 2019, 2027, 2031, 2039, 2043, 2055, 2071, 2079, 2111, 2115, 2139, 2155, 2163, 2179, 2183, 2191, 2199, 2207, 2211, 2227, 2235, 2251, 2255, 2271, 2279, 2287, 2291, 2299, 2311, 2315, 2323, 2331, 2355, 2371, 2375, 2391, 2399, 2403, 2419, 2427, 2435, 2443, 2451, 2467, 2471, 2479, 2487, 2495, 2503, 2507, 2515, 2523, 2535, 2559, 2567, 2575, 2587, 2595, 2611, 2619, 2635, 2651, 2659, 2663, 2667, 2683, 2687, 2691, 2715, 2731, 2735, 2743, 2751, 2767, 2771, 2779, 2787, 2795, 2811, 2819, 2823, 2831, 2839, 2847, 2863, 2871, 2895, 2911, 2919, 2935, 2943, 2959, 2967, 2983, 2991, 2999, 3003, 3035, 3043, 3051, 3067, 3071, 3079, 3083, 3087, 3111, 3127, 3135, 3167, 3171, 3187, 3191, 3195, 3219, 3235, 3243, 3259, 3263, 3271, 3275, 3287, 3295, 3303, 3315, 3347, 3351, 3359, 3363, 3379, 3387, 3395, 3411, 3423, 3439, 3447, 3459, 3467, 3471, 3487, 3495, 3511, 3515, 3531, 3547, 3551, 3559, 3563, 3571, 3575, 3599, 3607, 3611, 3619, 3635, 3643, 3647, 3655, 3671, 3675, 3711, 3719, 3723, 3739, 3743, 3751, 3763, 3771, 3783, 3799, 3807, 3827, 3835, 3851, 3855, 3871, 3883, 3891, 3899, 3907, 3911, 3915, 3947, 3951, 3963, 3971, 3983, 3991, 3999, 4015, 4031, 4039, 4047, 4063, 4071, 4087, 4095, 3549, 3573, 3585, 3601, 3609, 3621, 3637, 3641, 3649, 3657, 3673, 3677, 3681, 3693, 3701, 3705, 3737, 3745, 3761, 3765, 3781, 3789, 3801, 3817, 3825, 3861, 3893, 3901, 3909, 3917, 3921, 3929, 3933, 3957, 3965, 3981, 3989, 3993, 4009, 4017, 4033, 4041, 4053, 4069, 4077, 4093, 4097, 4105, 4113, 4125, 4157, 4161, 4177, 4181, 4189, 4197, 4205, 4217, 4221, 4245, 4261, 4265, 4273, 4277, 4293, 4313, 4321, 4329, 4353, 4361, 4373, 4377, 4385, 4393, 4401, 4417, 4425, 4449, 4457, 4461, 4469, 4477, 4489, 4495, 4511, 4519, 4523, 4527, 4539, 4555, 4563, 4587, 4603, 4607, 4615, 4631, 4639, 4643, 4647, 4655, 4679, 4683, 4699, 4707, 4719, 4743, 4767, 4783, 4787, 4791, 4799, 4803, 4811, 4819, 4827, 4835, 4843, 4851, 4887, 4903, 4907, 4915, 4923, 4935, 4967, 4971, 4979, 4987, 4991, 5007, 5015, 5031, 5055, 5071, 5079, 5087, 5091, 5099, 5103, 5131, 5139, 5151, 5167, 5171, 5175, 5211, 5227, 5231, 5235, 5251, 5259, 5267, 5275, 5287, 5295, 5311, 5319, 5335, 5351, 5355, 4833, 4849, 4857, 4865, 4881, 4889, 4893, 4909, 4913, 4921, 4937, 4941, 4961, 4973, 4977, 5001, 5009, 5013, 5025, 5049, 5081, 5085, 5109, 5125, 5141, 5149, 5157, 5173, 5181, 5197, 5201, 5209, 5213, 5221, 5229, 5253, 5269, 5277, 5285, 5301, 5325, 5349, 5357, 5365, 5381, 5385, 5401, 5409, 5421, 5437, 5441, 5445, 5481, 5513, 5521, 5525, 5549, 5557, 5561, 5569, 5573, 5577, 5601, 5609, 5617, 5625, 5655, 5687, 5699, 5707, 5715, 5739, 5747, 5755, 5763, 5779, 5783, 5787, 5799, 5807, 5811, 5827, 5831, 5847, 5855, 5863, 5879, 5883, 5899, 5907, 5923, 5927, 5931, 5943, 5959, 5967, 5999, 6007, 6011, 6015, 6031, 6039, 6063, 6079, 6083, 6099, 6115, 6123, 6139, 6147, 6159, 6167, 6175, 6199, 6203, 6207, 6215, 6231, 6247, 6251, 6267, 6275, 6287, 6291, 6307, 6323, 6327, 6351, 6367, 6371, 6379, 6383, 6391, 6407, 6415, 6423, 6431, 6439, 6447, 6463, 6471, 6483, 6491, 6495, 6511, 6519, 6535, 6543, 6555, 6587, 6595, 6603, 6619, 6623, 6631, 6639, 6647, 6659, 6663, 6671, 6679, 6683, 6691, 6695, 6711, 6719, 6723, 6743, 6751, 6759, 6771, 6787, 6795, 6819, 6827, 6831, 6863, 6867, 6891, 6899, 6903, 6927, 6935, 6951, 6967, 6971, 6975, 7011, 7035, 7067, 7075, 7087, 7095, 7127, 7131, 7139, 7151, 7155, 7187, 7191, 7215, 7247, 7251, 7259, 7275, 7299, 7311, 7319, 7327, 7335, 7359, 7375, 7391, 7399, 7411, 7415, 7423, 7431, 7439, 7447, 7455, 7487, 7491, 7507, 7511, 7527, 7543, 7551, 7563, 7571, 7579, 7595, 7619, 7627, 7635, 7651, 7659, 7683, 7699, 7703, 7707, 7723, 7727, 7731, 7743, 7759, 7763, 7771, 7779, 7787, 7795, 7803, 7827, 7835, 7843, 7859, 7867, 7871, 7879, 7883, 7887, 7903, 7911, 7927, 7931, 7947, 7959, 7975, 7999, 8007, 8023, 8031, 8039, 8043, 8059, 8063, 8071, 8079, 8087, 8091, 8115, 8131, 8139, 8147, 8151, 8183, 8195, 8211, 8243, 8247, 8255, 8271, 8283, 8299, 8307, 8331, 8339, 8347, 8355, 8371, 8379, 8415, 8397, 8413, 8421, 8437, 8453, 8461, 8465, 8473, 8481, 8497, 8505, 8043
