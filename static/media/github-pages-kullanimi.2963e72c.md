# Github Pages Kullanımı
Github Pages Github'ın ücretsiz olarak yaptığımız siteleri yayınlayabileceğimiz servisidir. Bizim için gerekli olan bir Github hesabı ve bir web projesidir. Biz burada react projesi kullanacağız. Hadi başlayalım.

İlk olarak Github'da bir repository oluşturuyoruz.

**{username}/blog** şekinde oluştutursanız  anasayfa 
**{username}.github.io/blog/** şeklinde gözükecek.  
 ### Ya da
**{username}/{username}.github.io** şekinde oluştutursanız  anasayfa **{username}.github.io** şeklinde gözükecek. 

___
Şimdi react projemize `yarn add -D gh-pages` ile paketimizi projemize ekliyoruz. Sonrasında **package.json** dosyasının script tagının altına iki satırı ekliyoruz.
```json
"predeploy": "npm run build",
"deploy": "gh-pages -d build"
```
Ve **package.json** dosyasına aşağıdaki satırı ekliyoruz. Bu sizin için oluşturduğunuz yukarıda belirttiğim gibi anasayfa çıktısı şeklinde olacak

```json
{
  "name": "my-app",
  + "homepage": "https://fatiherdogan01.github.io",
   ...
  "scripts": {
    ...
   + "predeploy": "yarn run build",
   + "deploy": "gh-pages -d build"
  },
  ...
  "devDependencies": {
     ...
    + "gh-pages": "^2.2.0",
    
  }
}

```
package.json görüntüsü sizin için de benzer bir görüntü alacaktır.
Şimdi master branch varsalıyan olarak geliyor ve biz **gh-pages** adında bir branch oluşturuyoruz.


# ![](https://pages.github.com/images/repo-settings@2x.png)
 Ayarlara tıklıyoruz

# ![](https://pages.github.com/images/launch-theme-chooser@2x.png)
Github Pages bölümüne gelip **source** 
kısmında oluşturduğumuz **gh-pages** branch'ini seçmeliyiz. 

`yarn deploy` komutunu çalıtırıp kodumuzu deploy ediyoruz.

## Artık siteye erişebiliriz.

Eğer repoyu **{username}/{username}.github.io**
şeklinde oluşturduysanız **source** kısmmında branch seçmemize izin vermiyor. Öncesinde böyle bir sorun yoktu bu bir bug olabir veya bilinçli bir şekilde kapatılmış olabilir. 

Tabiki de bunun bir çözümü var. Kodumuzu master branch'imize atmak. Daha önce eklediğimiz **deploy** script'ini aşağıdaki şekilde değiştiriyoruz.

```
"deploy": "gh-pages -b master -d build"
```
### ve
`yarn deploy` 

___

