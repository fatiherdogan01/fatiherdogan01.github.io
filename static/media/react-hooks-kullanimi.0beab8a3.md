# React Hooks Kullanımı
React Hooks, React 16.8 sürümü ile gelen sınıf yazmadan  state ve yaşam döngülerini yönetebilmemizi sağlayan fonksiyonlardır. Hook'lar class'ların içerisinde çalışmazlar. Biz bu Hook'lardan `useState` ve `useEffect`'i inceleyeceğiz. Daha fazla bilgiye bu [linkten](https://reactjs.org/docs/hooks-intro.html) ulaşabilirsiniz.
 ## State Hook’u
### useState kullanımı
`const [count, setCount] = useState(0);` **count** state'i tutan değişkenimiz, **setCount** state'i güncelleyecek fonksiyonumuz, **0** ise ilk değerimiz.

 Şimdi bir örneğe bakalım. Bu örnekte tıklandındığında sayaç 1 artıyor. İlk değerini sayaç olduğu için 0 verdik. Butona tıklandığında `setCount(count + 1)` fonkiyonu çalışıyor ve değeri 1 arttırıyor. 

```jsx
import React, { useState } from 'react';
function Example() {
// count bizim sayacımız olsun
const [count, setCount] = useState(0);
return (
<div>
 <p> {count} kere tıkladınız.</p>
 <button onClick={() => setCount(count + 1)}>
 Tıkla
 </button>
</div>
)}
```
Artık state yönetmek için class component yazmak gerekmiyor ve bu da kodun anlaşılabilir ve bakımının kolay olmasını sağlıyor. 
___
## Effect Hook’u
### useEffect kullanımı

`useEffect` bizim yaşam döngülerimizi yönetmemizi sağlayan bir fonksiyondur. `useEffect` kullanmadan bu işi `componentDidMount()` `componentDidUpdate()` `componentWillUnmount()` ile de yapabiliyoruz şimdi aşağıdaki kodları inceleyelim

```jsx
import React, { useState, useEffect } from 'react';

function Example() {
  const [count, setCount] = useState(0);

  useEffect(() => { 
    document.title = `${count} kere tıkladınız`;
  });

  return (
    <div>
      <p>{count} kere tıkladınız.</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}

```
`useEffect`‘i çağırdığınız zaman, React değişiklikleri DOM’a ilettikten sonra “effect” fonksiyonunu çağırmasını söylüyorsunuz. Effect’ler bileşenin içerisinde tanımlandığından state ve prop’lara erişebiliyor. Varsayılan şekliyle React effect’leri her render sonrasında çalıştırır. Bazen de farklı şekilde kullanabliriz. 

Şimdi useEffect kullanım farklarına bakalım
```jsx

useEffect(() => {
  //kod
});
```
kod componentler her render olduğunda çalışır.
```jsx
useEffect(() => {
  //kod
},[ ]);
```
kod sadece ilk yüklemede çalışır.
```jsx
useEffect(() => {
  //kod
},[deger]);
```
kod deger her değiştiğinde çalışır.
### Sonuç
 React 16.8 ve React Native 0.59 ve sonrası Hookları destekler. 100% geriye uyumludur. Hooklar fonksiyon componentlerde çalışır. Kodun anlaşılır olması için Hookları kullanabiliriz ancak tüm projeyi hooklara dönüştürmek pek mantıklı olmayacaktır. Tabi ki yeni bileşenleri Hooklar ile yazmak faydalı olabilir.
___







 
