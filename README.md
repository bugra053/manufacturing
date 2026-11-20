# ENS 208 — Manufacturing

Hocanın çalışma soruları ve **yalnızca gönderilen formül/tablo ekini** kullanan ayrı Manufacturing promptu.

## Kullanım

[online_prompt.txt — raw](https://raw.githubusercontent.com/bugra053/manufacturing/main/online_prompt.txt) dosyasını aç, **metnin tamamını** kopyala ve 7-Cal'de boş bir Custom Prompt slotuna yapıştır. Başlık `Manufacturing`; online tarama açık olmalı. Diğer derslerin promptlarını bu metinle değiştirme.

Çıktı düzeni:

- **F:** Yalnızca gerçekten kullanılacak sembolik formüller.
- **D:** Gerekli verilenler, katsayılar, üsler, düzeltme faktörleri ve birimler.
- **S:** Sayıları yerine koyma → gerekli ara işlemler → birimli kutulu sonuç.

Uzun açıklama, arama anlatımı, gereksiz integral veya formül listesi yok. Her istenen sonucun son sayısal işlemi gösterilir. Kullanılan tablo yalnızca `(S-7)` veya `(BU-4)` gibi küçük bir etiketle belirtilir. Modelin kendi kaynak gösterimleri platform tarafından ayrıca eklenebilir; bunların görünümü yalnızca promptla garanti edilemez.

## Kesin kaynak

[Hocanın ekinin birebir PDF'si](sources/appendix_formulas.pdf), kullanıcının verdiği `appendix ENS 208 Formulas 1.pdf` dosyasıdır; değiştirilmeden eklendi. **15 sayfa, 42 tablo başlığı**. Orijinal SHA256 değeri [source_manifest.json](data/source_manifest.json) ve [appendix/index.json](appendix/index.json) içinde.

- `appendix/tables/`: her tablonun ayrı raw metni; başlık ve dipnotlar korunur.
- `appendix/pages/`: orijinal 15 sayfanın PNG görüntüleri.
- `appendix/text/`: sayfa bazında tam metin çıkarımı.
- `data/verified_coefficients.json`: orijinal sayfalarla kontrol edilen 24 seçili katsayı kaydı; hesaplanan interpolasyonlar açıkça ayrılır. Bu küçük kayıt kümesi tam tablonun yerine geçmez.

Katsayılarda başka el kitabı, farklı baskı, üretici sitesi veya model hafızasına geçiş yok. Eksik değer uydurulmaz. Metinde birleşik sütunlar, kesirler, üsler ve kök dereceleri bozulabildiği için şüpheli durumda orijinal görüntü okunur.

## Çalışma dosyası

[sources/tutorial_calculations.pdf](sources/tutorial_calculations.pdf), `Tutorial Midterm 2027 fall ENS208 calculation task.pdf` dosyasının birebir kopyasıdır. **67 sayfa, 22 görev: 8 çalışılmış örnek + 14 alıştırma**. Dosya adı ile kapaktaki tarih farklı olduğundan kaynak korunmuş, sınav yılı tahmin edilmemiştir.

- `data/task_index.json`: görev numarası, konu, soru ve çözüm sayfaları, aday tablo bağlantıları.
- `tasks/`: her sorunun ayrı metni ve varsa hocanın çözüm sayfalarının metni.
- `tutorial/pages/`: 67 orijinal sayfanın görselleri; ölçü/çizim ve denklem kontrolü için.
- `tutorial/text/`: sayfa bazında raw metin.
- `course_reference.txt`: kaynak seçimi, birimler ve derse uygun hesap yöntemleri.
- `data/checked_examples.json`: altı bağımsız sayısal kontrol; bütün öğretmen çözümlerinin doğrulandığı veya belirli bir not alınacağı iddia edilmez.

## Önemli kontrol kuralları

Tabloya göre malzeme, takım türü, sertlik/dayanım ve ilerleme/kesme derinliği aralığı seçilir. Bilinmeyen ilerleme bulunduğunda varsayılan tablo aralığı doğrulanır. Katsayıların birim sistemleri karıştırılmaz. Aynı anda çalışan takımların gücü ve takım sayıları doğru toplanır. Devir/saniye, rpm, mm/dev, m/s, W/kW ve kg/s–kg/h dönüşümleri ayrı kontrol edilir.

Çalışılmış slaytlarda da yazım veya birim hataları vardır. Örnekler: S-13'ün10^8 çarpanı, 80mm'nin0.080m olması, tek delme sorusunun eta=.78 verisine rağmen çözümde.8 yazılması,14mm'nin.014m olması ve ortak başlık ilerlemesi için n_i*s_i eşitliği. İlgili kaynak notları [data/source_issues.json](data/source_issues.json) içinde. Bir düzeltme kaynak ve denklemle kesinleştirilemiyorsa kısa bir netleştirme sorusu gerekir.

Bazı alıştırmalarda gerçek belirsizlikler vardır:1.4.7'de takım ömrü '30mm' yazılmış;2.4.5'te orta delik grubu metinde4x10mm, parantezde4x15mm verilmiş. Prompt bunları sessizce değiştirmez. Bu notlar yalnızca ilgili soruyu etkilediğinde kullanılır; normal yanıtta uzun bir hata listesi basılmaz.

Repo public; raw içerikler token gerektirmez. Bu repo 7-Cal hesabını otomatik yapılandırmaz veya model API'sine istek göndermez. Modelin bir URL'yi görmesi, dosyayı gerçekten okuduğunu göstermez; gerçek erişim yoksa katsayı tahmin etmemesi istenir.
