# Manual de manipulação de dados

Contém os principais métodos usados no dia-a-dia para análise de dados, segmentação e tratamento dos dados.

```python
import numpy as np
import pandas as pd
```


#### GroupBy
```python
df_media = (
    df.groupby('coluna')['valor']
    .mean()
    .rename('avg')
)
```

#### Where
```python
new['coluna'] = new['coluna'].where(~(new['coluna2'] == 1),True)

#more performed
new['coluna'] = np.where(new['coluna2'] == 1, True, new['coluna'])
```

#### Loc + mask
```python
mask = (new['coluna2'] == 'referencia')
new.loc[mask, 'coluna'] = 'valor'
```

#### Valores nulos/blank
```python
new['coluna'].isna()
new['coluna'].notna()
pd.isna(new['coluna'])
new['coluna'] = new['coluna'].fillna(0).astype(int)
```

#### Coalesce
```python
new['coluna'] = new['coluna'].combine_first(new['coluna2'])
```

#### Tratamento strings
```python
new['coluna'] = new['coluna'].str.capitalize()
new['coluna'] = new['coluna'].str.extract(r'\b([0-9_]{8}\S)\b')
```

#### Datetime
```python
diferenca = abs((hora1 - hora2).total_seconds())
```
