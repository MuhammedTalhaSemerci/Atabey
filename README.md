## RestApi Hakkında Genel Bilgiler:

Request başlangıçta Route'a iletilir, sonrasında api_token ile authentication yapılır. Bağlantı controller'a iletilir ve ilgili controllerdaki metotlar requestin metot'una bağlı olarak ilgili fonksiyonları tetikler (get => index, post => show, put => update, delete => destroy).

## Authentication

Authentication benim araştırdığım kadarı ile 2 konsept ile gerçekleştirilebiliyor. 1. yöntemde "passport" ismi verilen bir yol izleniyor. İlk olarak normal bir kullanıcı giriş yapar gibi api aracılığıyla bir token üretiliyor, ve bu token ile aşağıda anlattığım işlemler yapılıyor. Yada 2. yol ile herhangi bir giriş yapılamksızın önceden edinilmiş bir api key ile sisteme erişilinebiliyor. Bu api örneği 2. yöntemi kullanarak çalışıyor.

Authentication ister get metodunda "/api/employee?api_token=d6vrU3fcTRN7hMT7BnD8oPbiEs1wJndKkTOGzdgrnbDeIbcvTQY9YnhVMejm" gibi yapılabilecekken istersekte header olarak gönderilebiliyor, "Accept" header'ı "application/json" olarak tanımlanır ve Authentication header'ı da "Bearer d6vrU3fcTRN7hMT7BnD8oPbiEs1wJndKkTOGzdgrnbDeIbcvTQY9YnhVMejm" gibi tanımlanır. Böylelikle auth. gerçekleşmiş olur.

## Get(index) metodu ve URL Yapısı:

Bu metot ile istenirse tüm verilere toplu olarak istenirse de sadece 1 indis'e ulaşılabilir:

Tüm veriler için "/api/employee" şeklinde yazarak ulaşabiliriz.
Bir veri için ise "/api/employee/15" gibi yazarak 15. indise erişmiş oluyoruz.

## Post(Show) metodu ve URL Yapısı:

Veriler Requestin body'si içerinde "x-www-form-urlencoded" biçiminde "/api/employee" urlsine iletilir. 4 veri iletilmeli bunlar şu şekilde; name(80,string), age(80,int), salary(10000,int), job(80,string)

## Update(update) metodu ve URL Yapısı:

Url yapısı aynı get metodunda bir indise erişmek ister gibi "/api/employee/15" şeklinde olmalı ve gönderilen verilen aynı post metodunda olduğu şekliyle iletilmeli.

## Delete(destroy) metodu ve URL Yapısı:

Aynı update de olduğu gibi url uzantımız "/api/employee/15" şeklinde olacak ancak burada herhangi bir ekstra veriye ihtiyaç duymuyoruz. Bu yüzden request'in body'sini boş bırakabiliriz.
      
