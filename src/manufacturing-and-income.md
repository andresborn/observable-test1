---
title: Análisis centro y periferia
toc: false
---

# Análisis de ingresos y manufactura entre el centro y la periferia

TODO: Make a nice graph from this https://thetricontinental.org/dossier-how-latin-america-can-delink-from-imperialism/


```js
const regions = FileAttachment("./data/regions.csv").csv({typed: true});
const corePeriphery = FileAttachment("./data/core_periphery.csv").csv({typed: true});

```

```js
const rangeYears = d3.sort(d3.union(regions.map((d) => d.year, 10)))
```

```js
// const yearIndex = view(
//   Inputs.range(
//     [0, rangeYears.length-1],
//     {step: 1,  format: (x) => rangeYears[x], }
    
//   )
// );
```

```js
// const year = rangeYears[yearIndex]
```

```js
const lastDefined = {
  reduceIndex(I, X) {
    for (let i = I.length - 1; i >= 0; --i) {
      const x = X[I[i]];
      if (x != null) {
        return x;
      }
    }
  }
}
```

### Diferencia de ingresos per cápita entre el centro y la periferia
```js
Plot.plot({
  marginBottom: 100,
  marginLeft: 100,
  fx: {padding: 0, label: null, tickRotate: 90, tickSize: 6},
  x: {axis: null, paddingOuter: 0.2},
  y: {grid: true},
  color: {legend: true},
  marks: [
    Plot.barY(corePeriphery, {y:"income", x: "system", fx: "year", fill: "system"}),
    Plot.ruleY([0])
  ]
})
```

### Diferencia de ingresos per cápita entre regiones
```js
Plot.plot({
  marginBottom: 100,
  marginLeft: 100,
  fx: {padding: 0, label: null, tickRotate: 90, tickSize: 6},
  x: {axis: null, paddingOuter: 0.2},
  y: {grid: true},
  color: {legend: true},
  marks: [
    Plot.barY(regions, {y:"income", x: "name", fx: "year", fill: "name"}),
    Plot.ruleY([0])
  ]
})
```

### Diferencia de valor agregado de manufactura per cápita entre el centro y la periferia
```js
Plot.plot({
  marginBottom: 100,
  marginLeft: 100,
  fx: {padding: 0, label: null, tickRotate: 90, tickSize: 6},
  x: {axis: null, paddingOuter: 0.2},
  y: {grid: true},
  color: {legend: true},
  marks: [
    Plot.barY(corePeriphery, {y:"manufacturing_per_capita", x: "system", fx: "year", fill: "system"}),
    Plot.ruleY([0])
  ]
})
```

### Producción de valor agregado de manufactura entre el centro y la periferia
```js
Plot.plot({
  marginBottom: 100,
  marginLeft: 150,
  fx: {padding: 0, label: null, tickRotate: 90, tickSize: 6},
  x: {axis: null, paddingOuter: 0.2},
  y: {grid: true},
  color: {legend: true},
  marks: [
    Plot.barY(corePeriphery, {y:"manufacturing", x: "system", fx: "year", fill: "system"}),
    Plot.ruleY([0])
  ]
})
```

### Core/Periphery Dataset
```js
corePeriphery
```

### Regions Dataset
```js
regions
```
