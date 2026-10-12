## Generowanie próby losowej
**Populacja generalna** jest modelowana zmienną losową $\xi$ o dystrybuancie $F(x)$. **Próba losowa** $x_{1},\dots,x_{n}$ to zaobserwowane wyniki $n$ pomiarów. **Szereg wariacyjny** to próba uporządkowana: 

$$x_{(1)}\leq x_{(2)}\leq\dots\leq x_{(n)}$$

Generowanie próby losowej z rozkładu $\mathcal{N}(m,\sigma^2)$ w języku Python implementujemy następująco:
```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
from scipy import stats

rng = np.random.default_rng(2026)
n, m, sigma = 100, 15, 3
x = rng.normal(loc=m, scale=sigma, size=n)
df = pd.DataFrame({"x": x})
print(df.head())
```
