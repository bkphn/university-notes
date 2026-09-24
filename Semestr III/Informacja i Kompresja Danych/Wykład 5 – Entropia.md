## Lematy pomocnicze
Lematem nazywamy pomocniczne twierdzenie, które ułatwia dowód bardziej złożonego twierdzenia.

W dowodach i analizach teorii informacji często wykorzystuje się następujące lematy:
> [!danger] Nierówność logarytmu naturalnego 
> $$\forall_{x \in \mathbb{R}} \ln x \le x - 1$$

>[!danger] Nierówność Jensena
>Dla funkcji ciągłej i wypukłej $f$ na przedziale $(\alpha, \beta) \subseteq (0, +\infty)$ oraz wag $\alpha_i \in \mathbb{R}_+$ takich, że $\sum_{i=1}^n \alpha_i = 1$, zachodzi:
$$ \sum_{i=1}^n \alpha_i f(x_i) \le f\left(\sum_{i=1}^n \alpha_i x_i\right) $$

>[!danger] Nierówność Gibbsa
>Dla $t_i, p_i \in \mathbb{R}_+$ oraz $\sum t_i = 1 = \sum p_i$, zachodzi:  $$ \sum_{i=1}^n p_i \log_2 t_i \le \sum_{i=1}^n p_i \log_2 p_i $$
## Entropia
Entropia $H$ alfabetu $\mathcal{A}$ określa ilość bitów przypadających na każdą literę układu. Można ją traktować jako miarę chaosu lub naszej niewiedzy o układzie (zgodnie z prawem ewolucji entropia układu domkniętego stale rośnie).

Dla źródła $S = (\mathcal{A}, P)$, gdzie $P = \{p_1, \dots, p_n\}$ to zbiór prawdopodobieństw stowarzyszonych z literami, entropię $H(\mathcal{A})$ definiujemy wzorem:
$$ H(\mathcal{A}) = -\sum_{i=1}^n p_i \cdot \log_2 p_i $$
**Entropia spełnia następujące własności:**
* **Nieujemność:** $$H(\mathcal{A}) \ge 0$$
* **Źródło martwe:** $$H(\mathcal{A}) = 0 \iff \exists_{a \in \mathcal{A}} : p(a) = 1$$
* **Ograniczoność (wzór Hartley'a):** $$H(\mathcal{A}) \le \log_2 n \iff p_1 = p_2 = \dots = p_n = \frac{1}{n}$$gdzie $n = |\mathcal{A}|$.
## Nadmiarowość układu
Jeżeli układ nie jest optymalny, mówimy o jego nadmiarowości $k(\mathcal{A})$. Nadmiarowość może być zarówno cechą negatywną (w kompresji danych) jak i cechą pozytywną (teoria kodów korygujących, teoria kodów nadmiarowych).
$$ k(\mathcal{A}) = 1 - \frac{H(\mathcal{A})}{H_{\text{max}}(\mathcal{A})} $$
gdzie maksymalna entropia wynosi $H_{\text{max}}(\mathcal{A}) = \log_2 n$.

Przykładowo, nadmiarowość języków europejskich wynosi około $50\%$ (np. j. francuski $\approx 2.96$ bit, j. hiszpański $\approx 3.98$ bit, j. niemiecki $\approx 4.10$ bit, j. rosyjski $\approx 4.36$ bit).
## Entropia dwóch źródeł
Dla dwóch źródeł $(\mathcal{A}, P_1)$ i $(\mathcal{B}, P_2)$ wpisujemy prawdopodobieństwo łączne $p(a_i, b_j)$ oraz warunkowe $p(a_i | b_j)$.
* **Entropia wspólna $H(\mathcal{A}, \mathcal{B})$** (ile średnio informacji niosą dwie wybrane wiadomości):
$$H(\mathcal{A}, \mathcal{B}) = -\sum_{i=1}^{|\mathcal{A}|} \left(\sum_{j=1}^{|\mathcal{B}|} p(a_i, b_j) \cdot \log_2 p(a_i, b_j) \right)$$
* **Entropia warunkowa cząstkowa:**
$$ H(\mathcal{A} | b_j) = -\sum_{i=1}^{|\mathcal{A}|} p(a_i | b_j) \cdot \log_2 p(a_i | b_j) $$
* **Entropia warunkowa pełna:**
$$ H(\mathcal{A} | \mathcal{B}) = -\sum_{i=1}^{|\mathcal{A}|} \left( \sum_{j=1}^{|\mathcal{B}|} p(b_j, a_i) \cdot \log_2 p(a_i | b_j) \right) $$
## Informacja własna i wzajemna
**Informacja własna** (entropia indywidualna) dana jest wzorem: $$I(a_i) = -\log_2 p(a_i)$$
Możemy zauważyć, że jeżeli zdarzenie $a$ jest pewne ($p(a)=100\%$), to jej wystąpienie niesie zerową informację ($I(a)=0$).

Prowadzący prof. Artemovych zaproponował autorskie twierdzenie o plotkach:

>[!danger] Twierdzenie o plotkach
>Bardziej prawdopodobna jest ta wiadomość, która niesie mniejszą ilość informacji.
>$$p(a) > p(b) \iff I(a) < I(b)$$

**Informacja wzajemna $I(\mathcal{A}; \mathcal{B})$:** miara zależności między zmiennymi, mówiąca, ile dowiadujemy się o sygnale $\mathcal{A}$, obserwując $\mathcal{B}$. Definiujemy ją wzorem: $$ I(\mathcal{A}; \mathcal{B}) = H(\mathcal{A}) - H(\mathcal{A} | \mathcal{B})$$ 
Informacja wzajemna spełnia własności:
- $I(\mathcal{A}; \mathcal{B})=H(\mathcal{A})+H(\mathcal{B})-H(\mathcal{A,B})$
- $I(\mathcal{A}; \mathcal{B})=I(\mathcal{B}; \mathcal{A})$
- $I(\mathcal{A}; \mathcal{B})\ge0$
- $I(\mathcal{A}; \mathcal{B})\le H(\mathcal{A})$
- $I(\mathcal{A}; \mathcal{A})=H(\mathcal{A})$
## Przepustowość kanału:
Dany jest kanał $k=(A, B)$, przepustowością kanału $k$ nazywamy wartość $C$ wyrażaną wzorem:
$$C = \max_P I(\mathcal{A}; \mathcal{B})$$
gdzie $P$ jest rozkładem prawdopodobieństw stowarzyszonym ze alfabetem $\mathcal{A}$. Przepustowość $C$ wyraża teoretyczną górną granicę prędkości z jaką można przesyłać informację przez kanał $k$ z dowolnie małym prawdopodobieństwem błędu.
## Twierdzenia Krafta, McMillana i Shannona 
> [!danger] Twierdzenie Krafta: 
>Dla alfabetu wejściowego $|\mathcal{A}|=n$ i wyjściowego $|\mathcal{B}|=u$, dla długości słów $l_1, \dots, l_n$ istnieje kod przedrostkowy $\iff \sum_{i=1}^n u^{-l_i} \le 1$.

>[!danger] Twierdzenie McMillana
>Każdy kod jednoznacznie dekodowalny spełnia nierówność Krafta.

>[!danger] Twierdzenie Shannona o średniej długości kodowej:
>Każdy jednoznacznie dekodowalny kod spełnia nierówność $l(C) \ge H(\mathcal{A})$.

>[!danger] Podstawowe Twierdzenie Shannona o kodowaniu bezpamięciowym
>Dla źródła bezpamięciowego dla każdego $n \in \mathbb{N}_+$ istnieje kod $\mathcal{A}^n \rightarrow \{0,1\}^*$ taki, że $H(\mathcal{A}) \le l(C) < H(\mathcal{A}) + \frac{1}{n}$.
