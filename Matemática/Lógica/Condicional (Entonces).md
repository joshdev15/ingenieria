---
isTrueTableChild: true
index: 3
operation: Entonces (->)
---

#math

El operador **Entonces - ->** : Si la primera proposición es verdadera, la siguiente también debe ser verdadera.

```dataviewjs
const data = {
    p: ['verdadero', 'verdadero', 'falso', 'falso'],
    q: ['verdadero', 'falso', 'verdadero', 'falso'],
    "p -> q": ['verdadero', 'false', 'verdadero', 'verdadero']
}

const rows = []
for (let i = 0; i < data.p.length; i++) {
    const p = data.p[i];
    const q = data.q[i];
    const pq = data["p -> q"][i];
    rows.push([p, q, pq])
}

dv.table(
    Object.keys(data),
    rows 
)
```

**p**: Está lloviendo
**q**: El suelo está mojado

 * Está lloviendo **entonces** el suelo está mojado: **Verdadero**
 * Está lloviendo **entonces** el suelo no está mojado: **Falso**
 * No está lloviendo **entonces** el suelo está mojado: **Verdadero**
 * No está lloviendo **entonces** el suelo no está mojado: **Verdadero**