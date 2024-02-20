#math

Una tabla de la verdad es una herramienta que se usa en la lógica
para evaluar si una proposición compuesta es verdadera.

En la siguiente tabla evaluaremos la proposición compuesta se
evaluará:

**p**: Está lloviendo
**q**: El suelo está mojado

```dataviewjs
const data = {
    p: ['verdadero', 'verdadero', 'falso', 'falso'],
    q: ['verdadero', 'falso', 'verdadero', 'falso'],
    "p -> q": ['verdadero', 'falso', 'verdadero', 'verdadero']
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

## Simbología de la tabla de la verdad

En una tabla de la verdad se hacen evaluaciones sobre proposiciones
lógicas, por tanto, existen los operadores lógicos

```dataviewjs
const data = {
    Operación: ['NO', 'Y', 'O', 'Entonces', 'Si y solo Si'],
    Simbolos: ['¬, ~', '∧', 'v', '->', '<->'],
}

const rows = []
for (let i = 0; i < data['Operación'].length; i++) {
    const p = data['Operación'][i];
    const q = data['Simbolos'][i];
    rows.push([p, q ])
}

dv.table(
    Object.keys(data),
    rows 
)
```


a continuación veremos una tabla de la verdad por operación:

[[Negación (No)]]
[[Conjunción (Y)]]
[[Disyunción (O)]]
[[Condicional (Entonces)]]
[[Bicondicional (Sí y solo sí)]]