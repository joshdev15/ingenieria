---
isTrueTableChild: true
index: 2
operation: Disjunción (∨)
---

#math

El operador **O - OR - ∨** : Es verdadera cuando al menos una de las proposiciones es verdadera.

```dataviewjs
const data = {
    p: ['verdadero', 'verdadero', 'falso', 'falso'],
    q: ['verdadero', 'falso', 'verdadero', 'falso'],
    "p ∨ q": ['verdadero', 'verdadero', 'verdadero', 'falso']
}

const rows = []
for (let i = 0; i < data.p.length; i++) {
    const p = data.p[i];
    const q = data.q[i];
    const pq = data["p ∨ q"][i];
    rows.push([p, q, pq])
}

dv.table(
    Object.keys(data),
    rows 
)
```

**p**: Está lloviendo
**q**: El suelo está mojado

 * Está lloviendo **o** el suelo está mojado: **Verdadero**
 * Está lloviendo **o** el suelo no está mojado: **Verdadero**
 * No está lloviendo **o** el suelo está mojado: **Verdadero**
 * No está lloviendo **o** el suelo no está mojado: **Falso**