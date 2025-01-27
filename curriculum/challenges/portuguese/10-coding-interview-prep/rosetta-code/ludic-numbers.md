---
id: 5ea281203167d2b0bdefca00
title: Números lúdicos
challengeType: 5
forumTopicId: 385282
dashedName: ludic-numbers
---

# --description--

Os números lúdicos estão relacionados aos números primos, pois são gerados por uma peneira semelhante à peneira de Eratóstenes, usada para gerar números primos.

O primeiro número lúdico é 1.

Para gerar os próximos números lúdicos, crie um array de números inteiros crescentes a partir do 2.

<code style='margin-left: 2em;'><span style='color:blue;font-weight:bold'>2</span> 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 ...</code>

(Gere o laço)

<ul>
  <li>Pegue o primeiro elemento do array resultante como sendo o próximo número lúdico <span style='color:blue;font-weight:bold'>2</span>.</li>
  <li>Remova cada <strong>2<sup>o</sup></strong> item indexado do array (incluindo o primeiro array).</li>
  <code style='margin-left: 2em;'><span style='color:blue;font-weight:bold;'><s>2</s></span> 3 <s>4</s> 5 <s>6</s> 7 <s>8</s> 9 <s>10</s> 11 <s>12</s> 13 <s>14</s> 15 <s>16</s> 17 <s>18</s> 19 <s>20</s> 21 <s>22</s> 23 <s>24</s> 25 <s>26</s> ...</code>
</ul>

<ul>
  <li>(Após alguns laços...)</li>
  <li>Pegue o primeiro elemento do array resultante como sendo o próximo número lúdico <span style='color:blue;font-weight:bold'>3</span>.</li>
  <li>Remova cada <strong>3<sup>o</sup></strong> item indexado do array (incluindo o primeiro array).</li>
  <code style='margin-left: 2em;'><span style='color:blue;font-weight:bold'><s>3</s></span> 5 7 <s>9</s> 11 13 <s>15</s> 17 19 <s>21</s> 23 25 <s>27</s> 29 31 <s>33</s> 35 37 <s>39</s> 41 43 <s>45</s> 47 49 <s>51</s> ...</code>
</ul>

<ul>
  <li>Pegue o primeiro elemento do array resultante como sendo o próximo número lúdico <span style='color:blue;font-weight:bold'>5</span>.</li>
  <li>Remova cada <strong>5<sup>o</sup></strong> item indexado do array (incluindo o primeiro array).</li>
  <code style='margin-left: 2em;'><span style='color:blue;font-weight:bold'><s>5</s></span> 7 11 13 17 <s>19</s> 23 25 29 31 <s>35</s> 37 41 43 47 <s>49</s> 53 55 59 61 <s>65</s> 67 71 73 77 ...</code>
</ul>

<ul>
  <li>Pegue o primeiro elemento do array resultante como sendo o próximo número lúdico <span style='color:blue;font-weight:bold'>7</span>.</li>
  <li>Remova cada <strong>7<sup>o</sup></strong> item indexado do array (incluindo o primeiro array).</li>
  <code style='margin-left: 2em;'><span style='color:blue;font-weight:bold'><s>7</s></span> 11 13 17 23 25 29 <s>31</s> 37 41 43 47 53 55 <s>59</s> 61 67 71 73 77 83 <s>85</s> 89 91 97 ...</code>
</ul>

<ul>
  <li><big><b> ... </b></big></li>
  <li>Pegue o primeiro elemento do array atual como sendo o próximo número lúdico <span style='color:blue;font-weight:bold'>L</span>.</li>
  <li>Remova cada <strong>L<sup></sup>-ésimo</strong> item indexado do array (incluindo o primeiro array).</li>
  <li><big><b> ... </b></big></li>
</ul>

# --instructions--

Escreva uma função que retorne todos os números lúdicos menores do que ou iguais ao número fornecido.

# --hints--

`ludic` deve ser uma função.

```js
assert(typeof ludic === 'function', '<code>ludic</code> should be a function.');
```

`ludic(2)` deve retornar um array.

```js
assert(Array.isArray(ludic(2)));
```

`ludic(2)` deve retornar `[1, 2]`.

```js
assert.deepEqual(ludic(2), [1, 2]);
```

`ludic(3)` deve retornar `[1, 2, 3]`.

```js
assert.deepEqual(ludic(3), [1, 2, 3]);
```

`ludic(5)` deve retornar `[1, 2, 3, 5]`.

```js
assert.deepEqual(ludic(5), [1, 2, 3, 5]);
```

`ludic(20)` deve retornar `[1, 2, 3, 5, 7, 11, 13, 17]`.

```js
assert.deepEqual(ludic(20), [1, 2, 3, 5, 7, 11, 13, 17]);
```

`ludic(26)` deve retornar `[1, 2, 3, 5, 7, 11, 13, 17, 23, 25]`.

```js
assert.deepEqual(ludic(26), [1, 2, 3, 5, 7, 11, 13, 17, 23, 25]);
```

# --seed--

## --seed-contents--

```js
function ludic(n) {

}
```

# --solutions--

```js
function ludic(n) {
  const makeArr = (s, e) => new Array(e + 1 - s).fill(s).map((e, i) => e + i);

  const filterAtInc = (arr, n) => arr.filter((e, i) => (i + 1) % n);

  const makeLudic = (arr, result) => {
    const iter = arr.shift();
    result.push(iter);
    return arr.length ? makeLudic(filterAtInc(arr, iter), result) : result;
  };

  const ludicResult = makeLudic(makeArr(2, n), [1]);

  return ludicResult;
}
```
