## React Router Kullanımı
React Router sayfalar arasında geçiş yapmamızı sağlayan bir pakettir. Eğer bir react projesi geliştiriyorsak mutlaka kurulması gereken bir pakettir.
`yarn add react-router-dom` ile paketi projemize dahil ediyoruz.


```jsx
import React from "react";
import {
  BrowserRouter as Router,
  Switch,
  Route,
  Link
} from "react-router-dom";

export default function App() {
  return (
    <Router>
      <div>
         <Link to="/">Home</Link>
         <Link to="/about">About</Link>    
         <Link to="/user">User</Link>
        <Switch>
         <Route path='/about' component={About} />
         <Route path='/user' component={User} />
         <Route path='/' component={Home} />
        </Switch>
      </div>
    </Router>
  );
}

```
Şimdi yukarıdaki kodu inceleyelim. Home, About ve User komponentlerinini import edildiğini varsayalım.
### Router
 `<Router> </Router>` tagını  projenin ana komponentini sarmalayacak şekilde  bir kez kullanıyoruz. Artık tüm projeyi kapsıyor. Bu tagı Switch içinde kullandığımız **Route**  karıştırmamak gerekiyor.
 ### Route
 Route ile **path**'da belittiğimiz yola hangi komponenti yönlendireceğini söylüyoruz.
 ```jsx
   <Route path='/about' component={About} />   
```

### Switch
 `<Switch></Switch>` tagı  switch / case yapısı gibi çalışır ve sırayla eşleşmeyi kontrol eder. **Örneğin** About linkine tıkladığımızda sırayla kontrol ediyor ve bizi about sayfasına yönlendiriyor. Oldukça basit bir yapısı var. 

Eğer bunların dışında bir sayfaya yönlendirmek istiyorsak `<Route component={NotFound}/>`  gibi bir notFound sayfasına yönlendirebiliriz. Bunu ilk sıraya yazsaydık direk biz notFound sayfasına yönlendirecekti tabi ki bu istedğimiz birşey değil.
 ### Exact Parametresi
 **exact** parametresi ile eşleşmenin birebir olamasını söylüyoruz.
 ```jsx
   <Route exact path='/about' component={About} />   
```

| **path**|	**location.path**	|**exact** | **eşleşme**| 
| :---    |:---               |:---:      | :---:     |
|/about   |/about/me          | `true`   | hayır      |
|/about   |/about/me          | `false`  | evet       |

yukarıdaki tabloda görüldüğü gibi **exact** parametresi verdiğimizde birebir eşleşme bekliyor ve yönlendirme gerçekleşmiyor.

___

# Dimamik yönlendirme
Tabi ki gerçek hayatta tüm path'leri tek tek tanımlayamayız. Bunun için dinamik yönlendirmeyi kullanmalıyız. 
```jsx
 <Route path='/user/:id' component={User} />
```
Yönlendirmeye `:id` ile  bir paramametre geçiyoruz. Artık `/user`dan sonra istediğimiz parametreyi geçebiliriz.

```jsx
<Link to="/user/100">User</Link>
```
ile 100 numaralı kullanıcıya erişebiliriz. Peki bunu nasıl yapacağız birlikte bakalım.

```jsx
export default function User({match}) {
  console.log(match)
 return(
   <div> </div>
 )
}
```

```js
// output
{path: "/user/:id", url: "/user/100", isExact: true, params: {…}}
isExact: true
params: {id: "100"}
path: "/user/:id"
url: "/user/100"
 ```
User komponentimize parametre olarak geçtiğimiz **match** objesi ile gönerdiğimiz parametre özelliklerine erişebiliyoruz.
Tabi ki bizim amacımız gönderdiğimiz parametreye erişmek. `match.params.id` ile kolayca erişebiliriz
 ```jsx
 console.log(match.params.id) 
 // output:100
 const userId = match.params.id
  ```
  Artık elimizde **userId** adında bir değişkenimiz var bununla veritabanı sorugusu yapabilir veya lokal dataya erişebiliriz.
 ___
