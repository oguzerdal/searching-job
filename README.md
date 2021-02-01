Bu frontend projesi Vue.js Cli ile geliştirilmiştir.
Projenin amacı kullanıcıların iş ilanları içerisindeki bir anahtar kelimeye göre (şehir,posizyon ismi, şirket ismi vb.) ilanı bulup o ilanın detaylarını görüntüleyebilmesini amaçlıyor. 
Projeye routing yapısı sağlamak için Vue Router kullanılmıştır. 
Veriler localhost:3000 portunda koşan json-server üzerinden bir fake api ile localhost:8000 portundan dinlemesiyle uygulamaya transfer oluyor. 
Verilerin çekilebilmesi için ilk önce şu komutla "json-server --watch src/fake_api/db.json" json server ayağa kaldırılması gerekir. 
Projenin tasarımında ise Bootstrap kullanılmıştır. 
