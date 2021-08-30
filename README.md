
![ASD](https://img.shields.io/badge/VS%202019-Visual%20Studio-blueviolet) ![ASD](https://img.shields.io/badge/ASP.NET%20CORE-.NET%205-blue) ![](https://img.shields.io/badge/SQL%20SERVER%202019-Express-yellow) 



## 1️⃣ Cache Nedir ?

**Önbellek** olarak bilinen "cache", internet üzerinden yaptığınız aramaların bir süreliğine **cihazının belleğinde depolanması** anlamına gelir. Önbellek, kaydetmiş olduğu geçici veriler sayesinde bilgisayarınızın web sitelerini daha hızlı yüklemesine yardımcı olur. Cache’i bir **hafıza bankası** olarak da değerlendirebilirsiniz.

Cache, **internete bağlı her türlü cihazda** bulunur. İster telefondan girdiğiniz bir uygulamada isterseniz de bilgisayarınız üzerinden bağlandığınız tarayıcıda, önbellek verileri mutlaka depolanır. Girmiş olduğunuz web sayfalarının fotoğraflarından metinlerine kadar geçici olarak kayıt altına alan Cache, aslında son derece kullanıcı dostu bir sistemdir. 

## 2️⃣ Cache ne işe yarar?
<p align="center">
<img src="https://i.ibb.co/NSxLGBs/2e7c3f8a4972954646cb7822dcf78d1bffac32d0.jpg" style="zoom:50%;" />
</p>
Cache, daha önce de belirtmiş olduğumuz gibi girdiğiniz bir web sayfasının ya da uygulamanın HTML sayfaları gibi önemli verileri kendi deposuna kaydederek, bu sitelere **bir sonraki ziyaretinizde** her şeyin daha hızlı ve kolay bir şekilde yüklenmesini sağlar. 

## 3️⃣**Cache Türleri** 

Farklı cachle türleri ve kategorizelendirmeleri olmakla birlikte en genel bilinen cache türleri Client side caching, Server side caching ve CDN(Content Delivery Network) cachingdir.

## 🅰️***Client Side Cache***

Client side caching ile web browseriniz sayfanın nasıl göründüğünü hatırlar ve sunucuya websiteyi tekrar yollaması için istekte bulunmaz. Client side caching’te veriler kullanıcının kişisel bilgisayarında tutulur ve yer kaplar. Bu tüm network sürecini aradan çıkararak zaman ve bandwidth tasarrufu sağlatır. Ancak, websiteye ilişkin bilgiler server bazında değiştirilirse sıkıntı başlar çünkü browserınızın tuttuğu website bilgileri artık eski ve güncel değildir. Bu da aslında insanların size belli aralıklarla cacheninizi temizlemenizi söylemesinini sebebidir. Cachei temizleyerek sunucudan güncel versiyon talebinde bulunuruz.

##  :b: ***Server Side Caching***

Server side caching ise uygulama tarafından belli bir kaynaktan (database, webservice) çekilen, birden fazla clientla paylaşılan ve değişme ihtimali düşük olan verinin kaynağa (database server, webservice service) tekrar tekrar istekte bulunup çekilmesi yerine, ilk istekten sonra uygulama sunucusunun raminde tutulup, her çağırıldığında uygulama sunucusunun raminden dönmesidir. Yani server-side cachle genellikle expensive tekrar eden farklı clientlara aynı contenti sunan database operasyonlarınında kullanılır ve data serverda cachlenir.
<p align="center">
<img src="https://i.ibb.co/Scw33rZ/0-O2upb53-F-HWVLc-Gt-300x127.png" alt="0_O2upb53F-HWVLcGt-300x127" style="zoom:150%;" />
</p>

##  :cl:  Content Delivery Network (CDN) Cache

CDN önbelleğe alma, daha geniş bir veri depolama biçimidir. CDN önbellekleme ile, genel olarak dağıtılan proxy sunuculara statik web sitesi içeriği eklenir. Bu, dünyanın her yerinden ziyaretçilerin site içeriğinizi daha hızlı indirmesini sağlayarak sitenizin yükleme süresini hızlandırır. CDN önbelleğe alma aynı zamanda web sitesi sahiplerinin maliyetleri azaltmasına yardımcı olur, orijinal sunucudan baskı alır ve odağı ziyaretçilerin yerel olarak verilere erişebileceği küresel olarak bulunan daha küçük yerel sunuculara yerleştirir.

## :four: Benim kullandığım cache örnekleri
<p align="center">
<img src="https://i.ibb.co/9Tc7Xnq/distributed-caching-in-aspdotnet-core-with-redis-1.png" alt="1126dea7-099f-4191-b18b-c3691cd34b47" style="zoom:50%;" />
</p>

## 🅰️ In-Memory Caching

In-Memory Cache uygulama ile ilgili verilerin uygulamanın çalıştığı uygulama sunucusunun ram belleğinde tutulması işlemidir. Tutabileceğimiz cache boyutu uygulama sunucusunun ram miktarıyla doğru olarantılıdır.

Uygulamamızın tekbir instance varsa problemsiz bir şekilde kullanılır.

Uygulamamızın birden fazla instance varsa ve bu instancelara bir “load balancer” yönlendirme yapıyorsa uygulamaya istek yapan kullanıcı farklı zamanlarda farklı instance lara yönlendirilebilir. Bu durumda kişi farklı zamanlarda farklı cachelere ulaşacağından her isteğinde farklı bir veri görür. Bu tutarsızlığı çözmek için “load balancer” üzerinden “sticky session” özelliği ile uygulamaya istek yapan kullanıcı devamlı aynı uygulama instance ına gönderilebilir. Sticky Session cokie veya Ip’ye göre yönlendirme yapabilmektedir.

Eğer uygulamamız birden fazla sunucu üzerinde çalışıyorsa In-Memory Cache yerine Distributed Cache kullanmak daha doğru olacaktır.

## :b:Disributed Caching

Distributed Cache yönteminde, Cache dataları uygulamanın ayağa kalktığı host işletim sisteminin ram belleğinde tutulmaz. Bu yöntemde cache dataları ayrı bir cache service inde tutulur.

**Avantajları Nelerdir?**

- Veri tutarsızlığının önüne geçilmiş olur.
- Uygulamanın ayağa kaktığı host bilgisayar resetlendiğinde cache verileri silinmez.

**Distributed Caching Dezavantajları Nelerdir?**

- Farklı bir service ‘den cache dataları istendiği için In-Memory Cache yöntemine göere daha yavaşdır.
- In-Memory Cache yöntemine göre kullanımı daha zordur.

> ### Veritabanları Hakkında
>
> Veritabanı dizinleri, doğru kullanıldığında uzun bir yol kat edebilir. Sorgularınızın zaman karmaşıklığını ve verimliliğini etkili bir şekilde artıracaklar. Ancak, diskten veri döndürmek için çok fazla iş yapmak zorunda olduğundan, veritabanınızda yine de performans sorunlarıyla karşılaşabilirsiniz.
>
> Çoğu SQL veritabanlarından çok daha kolay bir şekilde birden fazla sunucu arasında ölçeklenecekleri için, genellikle MongoDB veya Cassandra gibi bir NoSQL veri tabanı tercih edebilir. Bu, iş yükünü azaltmak ve ihtiyacınız olan performansı elde etmek için soruna daha fazla sunucu atmanıza olanak tanır. Ve bu sizin için doğru seçim olabilir veya olmayabilir. Ancak hem SQL hem de NoSQL veritabanları hala aynı sorundan muzdariptir: veriler diskte depolanır ve diskten erişilir.


<img  width ="100" src="https://i.ibb.co/yY3Lq2x/redis.png" alt="redis" align=”left” /> <p>Redis, çoğunlukla dağıtılmış önbellek olarak kullanılan bir bellek içi veri deposudur. Verilerinize vahşice hızlı erişim sağlamak için tasarlanmış çeşitli verimli veri yapıları sunar. Genellikle yapmak isteyeceğiniz şey, sık erişilen verileri Redis'te depolamaktır, böylece veriler istendiğinde veritabanınız yerine önbellekten gelebilir. Ardından, verilerinizde her değişiklik yapıldığında ilgili önbelleği geçersiz kılabilirsiniz, böylece önbelleğinizi güncel tutabilirsiniz. 

Redis, sunucu yeniden başlatıldığında önbelleğin kaybolmaması için diskte kalıcı olma seçeneğine de sahiptir. Ayrıca Redis, önbelleği birden çok sunucuya yayan bir kümede de oluşturulabilir. Teknik olarak Redis, birincil veritabanınız olarak da kullanılabilir, ancak daha sık olarak, kalıcı veriler için tasarlanmış daha zengin özelliklere sahip veritabanlarındaki yükü azaltmak için onu bir önbellek olarak kullanırız.

Önbelleğe almanın yoğun bir şekilde kullanılabileceğini bilmek, diğer hususları da gerçekten değiştirebilir. Yukarıda NoSQL veritabanlarının kolay ölçeklenebilirliğinden bahsetmiştim. Ancak Redis, önbelleğe alma yoluyla veritabanı iş yükünüzün yüzde 95'ini ortadan kaldırıyorsa, aslında tek bir SQL veritabanı örneğine bağlı kalmak uygun olabilir.

StackOverflow ekibi, diğer StackExchange web sitelerinin yanı sıra stackoverflow.com'u hızlandırmak için yıllardır büyük bir etkiyle kullandıklarından, Redis ile olan deneyimleri hakkında bazı ilginç makaleler yayınladı.
</p>
[StackOverflow'tan Nick Craver, 2019'daki tipik Redis kullanımını açıklamaya devam ediyor:](https://nickcraver.com/blog/2019/08/06/stack-overflow-how-we-do-app-caching/)

- *Redis fiziksel sunucularımız 256 GB belleğe sahiptir, ancak 96 GB'tan daha az kullanılır.*
- *Günde 1.586.553.473 komut işlenir (replikalar nedeniyle tüm örneklerde 3.726.580.897 komut ve saniyede 86.982 tepe).*
- *Tüm sunucu için ortalama %2,01 CPU kullanımı (%3,04 tepe noktası) (en aktif örnek için bile < %1).*
- *124.415.398 etkin anahtar (replikalar dahil 422.818.481).*
- *Bu sayılar 308.065.226 HTTP isabetine (64.717.337'si soru sayfasıydı) aittir.*

Gördüğünüz gibi, günde 1,5 milyardan fazla Redis komutuyla bile, Redis sunucuları yalnızca yüzde 2 CPU kullanımıyla zar zor ter döküyor.

StackOverflow örneği, kullanıcı tabanının büyüklüğü nedeniyle harika. Hem WWT içinde hem de dışında konuştuğum herkesin Redis hakkında söyleyecekleri çok olumlu şeyler oldu. Yetenekleri etkileyicidir ve bir ton sunucu kaynağı olmadan uygulamanız ile şaşırtıcı miktarlarda verime izin verebilir. 

Redis'in uygulamanız için uygun olup olmadığını belirlemek için bizimle konuşun. Uygulamanızın etkili bir şekilde ölçeklenmesini sağlamak için bir önbelleğe alma stratejisi uygulayacak uzmanlığa sahibiz.


<details>
<summary><b>Kaynaklar</b> :mag: </summary>
<p>

[Kaynak 1](https://www.wwt.com/article/the-power-of-distributed-caching-with-redis/) :+1:
[Kaynak 2](https://www.webtekno.com/cache-nedir-h99461.html) :+1:
[Kaynak 3](https://blexin.com/en/blog-en/distributed-cache-in-asp-net-core/) :+1:
[Kaynak 4](http://cagataykiziltan.net/tr/cache-ve-cache-turleri/) :+1:
[Kaynak 5](https://docs.microsoft.com/tr-tr/aspnet/core/performance/caching/memory?view=aspnetcore-5.0) :+1:
</p>
<p>bir çok makale :bowtie: </p>

![Medium](https://img.shields.io/badge/Medium-12100E?style=for-the-badge&logo=medium&logoColor=white)

<p>bir çok video :eye_speech_bubble: </p>

![YouTube](https://img.shields.io/badge/youtube-%23FF0000.svg?style=for-the-badge&logo=YouTube&logoColor=white)

<p>bir çok başlık :page_with_curl: </p>

![Stack Overflow](https://img.shields.io/badge/-Stackoverflow-FE7A16?style=for-the-badge&logo=stack-overflow&logoColor=white)
