---
isTrueTableChild: true
index: 0
operation: Negación (¬)
---

#math

La negación **No - NOT - ¬** en términos lógicos invierte el valor de la proposición actual. A continuación un ejemplo:

```dataviewjs
const data = {
    p: ['verdadero', 'falso'],
    '¬p': ['falso', 'verdadero'],
}

const rows = []
for (let i = 0; i < data.p.length; i++) {
    const p = data.p[i];
    const q = data['¬p'][i];
    rows.push([p, q])
}

dv.table(Object.keys(data), rows)
```

### Ejemplo gramático

**p**: Está lloviendo

* Está lloviendo: Verdadero
* No (está lloviendo): Falso