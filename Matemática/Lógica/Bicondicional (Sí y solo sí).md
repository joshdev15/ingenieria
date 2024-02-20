---
isTrueTableChild: true
index: 4
operation: Bicondicional (<->)
---
#math

El operador **Sí y solo sí - <->** : Si la ambas proposiciones son verdaderas.

```dataviewjs
const data = {
    p: ['verdadero', 'verdadero', 'falso', 'falso'],
    q: ['verdadero', 'falso', 'verdadero', 'falso'],
    "p <-> q": ['verdadero', 'false', 'false', 'verdadero']
}

const rows = []
for (let i = 0; i < data.p.length; i++) {
    const p = data.p[i];
    const q = data.q[i];
    const r = data["p <-> q"][i];
    rows.push([p, q, r])
}

dv.table(
    Object.keys(data),
    rows 
)
```

**p**: Está lloviendo
**q**: El suelo está mojado

 * Está lloviendo **si y solo si** el suelo está mojado: **Verdadero**
 * Está lloviendo **si y solo si** el suelo no está mojado: **Falso**
 * No está lloviendo **si y solo si** el suelo está mojado: **Falso**
 * No está lloviendo **si y solo si** el suelo no está mojado: **Verdadero**