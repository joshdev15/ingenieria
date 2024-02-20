---
isTrueTableChild: true
index: 1
operation: Conjunción (∧)
---

#math


El operador **Y - AND - ∧** : Es verdadero si ambas proposiciones son verdaderas. Es falso si existe un solo valor falso o ambos.

```dataviewjs
const data = {
    p: ['verdadero', 'verdadero', 'falso', 'falso'],
    q: ['verdadero', 'falso', 'verdadero', 'falso'],
    "p ∧ q": ['verdadero', 'falso', 'false', 'falso']
}

const rows = []
for (let i = 0; i < data.p.length; i++) {
    const p = data.p[i];
    const q = data.q[i];
    const pq = data["p ∧ q"][i];
    rows.push([p, q, pq])
}

dv.table(
    Object.keys(data),
    rows 
)
```

**p**: Está lloviendo
**q**: El suelo está mojado

 * Está lloviendo **y** el suelo está mojado: **Verdadero**
 * Está lloviendo **y** el suelo no está mojado: **Falso**
 * No está lloviendo **y** el suelo está mojado: **Falso**
 * No está lloviendo **y** el suelo no está mojado: **Falso**