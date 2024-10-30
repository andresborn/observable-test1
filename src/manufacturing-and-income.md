---
title: Rosling test
toc: false
---

# The health and wealth of nations
Live demo from an episode of [Fun Fun Function](https://fff.dev). Source code and explanation [here](https://github.com/funfunfunction/fff-health-and-wealth-of-nations).
```js
const manufacturingAndIncome = FileAttachment("./data/out.csv").csv({typed: true});
```

```js
const rangeYears = d3.sort(d3.union(manufacturingAndIncome.map((d) => d.year, 10)))
```

```js
const yearIndex = view(
  Inputs.range(
    [0, rangeYears.length-1],
    {step: 1,  format: (x) => rangeYears[x], }
    
  )
);
```

```js
const year = rangeYears[yearIndex]
```

```js
Plot.plot({
  grid: true,
  aspectRatio: undefined,
  height: 600,
  width: 900,
  color: {legend: true, type: "categorical", scheme: "accent"},
  x: {domain: [new Date('1950'), new Date('2030')], value: "year", transform: (y) => new Date(String(y))},
  y: {type: "log", domain: [200, 100e3]},
  marks: [
    Plot.dot(manufacturingAndIncome, {x: "year", y: "income", stroke: "name"}),
    Plot.dot(manufacturingAndIncome, {x: "year", y: "manufacturing_per_capita", stroke: "name"})
  ]
})
```

### Dataset
```js
manufacturingAndIncome
```
