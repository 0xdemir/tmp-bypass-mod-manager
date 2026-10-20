<div align="center">

![TruckersMP Mod Manager Bypass](assets/truckersmp-mod-banner.png)

# TruckersMP Mod

### TruckersMP Mod Manager Bypass

Local mods and vehicle compatibility for Euro Truck Simulator 2.

Euro Truck Simulator 2 için yerel modlar ve araç uyumluluğu.

![Version](https://img.shields.io/badge/version-1.0.32-27c8bb)
![Platform](https://img.shields.io/badge/platform-Windows_x64-0078d4)
![Distribution](https://img.shields.io/badge/distribution-single_EXE-555555)

**[Download v1.0.32 / v1.0.32 indir](https://github.com/0xdemir/tmp-bypass-mod-manager/releases/download/v1.0.32/TMP.Mod.exe)**

[English](#english) · [Türkçe](#turkce)

</div>

---

<a id="english"></a>

## English

TruckersMP Mod is a desktop launcher for using local ETS2 mods with TruckersMP and accessing the in-game Mod Manager.

Download stable **v1.0.32** from [Releases](https://github.com/0xdemir/tmp-bypass-mod-manager/releases/latest). Save `TMP.Mod.exe` as `TMP Mod.exe`, or extract `TMP-Mod-1.0.32.zip`. Both contain the same application. A [repository copy](TMP%20Mod.exe) is also available. No separate compatibility mod is required.

### New in v1.0.32

Known original parts attached from other vehicle models through save editing now keep their identity on supported stock trucks. Earlier versions could replace them with the truck's defaults or omit them. Part order, repeated parts and attachment data are preserved. Unsupported local mod vehicles continue to use the selected truck, bus or car appearance.

Replaying a reported Scania S configuration now preserves all 88 parts; previously, 19 were replaced and two were omitted. Checks cover the 26 supported truck models in the current database with all three appearance choices. Live multiplayer rendering of this update still needs confirmation.

### New in v1.0.31

Encrypted description files in ZIP-based mods no longer stop preparation with a “password required for extraction” error. For ZIP entries and loose files with known names, preparation reads only `.sii` and `.sui` definitions. Descriptions, images and other assets are skipped during content reading. Existing handling for unnamed HashFS v1 entries is unchanged.

If a definition is encrypted, it is recorded in the preparation report and excluded from merging across all sources. Other definitions can still be processed. This does not decrypt the mod or guarantee compatibility with its encrypted definitions.

### What changed since v1.0.17

- Added truck, bus and car choices for how unsupported mod vehicles appear to other players.
- Fixed missing dealer brands and incorrect brand/vehicle associations in the tested mod setup.
- Fixed the crash when returning to the dealer after configuring a vehicle. Two consecutive configuration/return cycles passed the user's live test in v1.0.29; later releases keep that fix.
- Preparation reuses its cache across launches. In a v1.0.32 check with the installed mod library, the first scan took about 7 minutes 11 seconds; the next preparation took 23.8 seconds and produced the same payload. Times depend on the mod library. Updates or mod changes can require another full scan.
- v1.0.30 adds an explanation above the vehicle choices: stock vehicles keep their own make and model.

Compatible accessory database (ADB) updates are still detected automatically. If the database changes during or after preparation, prepare a new session. A different database format or changed game/TruckersMP code signatures may require an application update.

### How the three vehicle choices work

Choose **Karşı tarafta görünen araç** before starting the watchers. This sets the network representation of an unsupported local mod vehicle. You continue to see your own mod's model and interior; other players see the selected supported vehicle.

| Choice in the application | Other players see |
| --- | --- |
| **Tır · Volvo FH16** | Volvo FH16 (`volvo.fh16_2012`) |
| **Otobüs · TruckersMP** | The supported TruckersMP bus (`t16shd`) |
| **Araba · Scout** | Scout / Škoda Superb (`skoda.superb`) |

For example, choose **Araba · Scout** for a car mod to represent it as a Scout, or **Otobüs · TruckersMP** for a bus mod to represent it as the supported bus. This choice applies to unsupported mod vehicles throughout that session; it does not automatically switch based on the type of each mod. Start a new session to change it.

**Stock ETS2 vehicles keep their own make and model.** A stock Scania stays a Scania even with Volvo selected. Vehicles already recognized by TruckersMP also keep their supported identity. The choice does not grant access to restricted vehicles or parts; client and server rules still apply. Compatibility depends on the mod's definitions and dependencies.

On supported stock trucks, original parts already recognized by TruckersMP keep their identity and attachment data even when save editing places them on a different model. Unknown local parts still follow the existing mapping rules.

### Requirements

| Component | Requirement |
| --- | --- |
| Operating system | 64-bit Windows |
| Game | Installed ETS2; tested build: **1.61.1.9s** |
| Multiplayer | Installed official TruckersMP launcher; local core version: **0.7.8.3** |
| Permissions | Run `TMP Mod.exe` as administrator |
| Extra installation | No additional runtime installation required |

### Install and start

1. Close ETS2 and any older TMP Mod windows before preparing a new session.
2. Place `TMP Mod.exe` in `%APPDATA%\TruckersMP`.
3. Right-click `TMP Mod.exe`, select **Run as administrator** and approve the Windows prompt. Then choose the vehicle appearance described above.
4. Click **İzleyicileri başlat** (Start watchers).
5. Wait for **OYNA için hazır** (Ready to play).
6. Click **TruckersMP’yi aç**, then press **PLAY / OYNA** in the official TruckersMP launcher.
7. Select your mods and vehicle in the game.

Closing the TMP Mod window leaves an active adaptation running. Exit the game to end that session. **Beklemeyi iptal et** cancels waiting before the game starts. Use **Günlükleri aç** to inspect a failed run.

### Antivirus alerts and permissions

If your antivirus blocks or quarantines `TMP Mod.exe`, check that you downloaded it from this repository's [Releases](https://github.com/0xdemir/tmp-bypass-mod-manager/releases/latest) page and that its SHA-256 matches the value under [File integrity](#file-integrity--dosya-bütünlüğü). The linked [VirusTotal report covers the previous v1.0.31 EXE](https://www.virustotal.com/gui/file/7068f9e0c52e38e11e0eb06fa68679b0ffb2dcd83113f6094a4d679c7a6dc1d9). v1.0.32 has a different hash; check any scan report against the hash of your downloaded file.

If you trust the verified file and decide to run it, allow that specific file through your antivirus's quarantine or protection history screen. Keep antivirus protection enabled. The report applies to the EXE with the linked hash; scan results can change and do not guarantee safety.

### Checks and troubleshooting

For v1.0.32, 22 Python policy/database tests, 14 camera/content-reading tests and 58 controller tests passed. Each of the three appearance choices passed 46 compiled native scenarios, including preservation of the reported 88 parts and their original objects. Cross-model part checks passed for 26 supported truck models across 78 model/choice combinations. Independent code review and compiled package checks passed. The earlier dealer fix passed 19 dealer/transaction test groups; the user confirmed correct dealer associations and two successful configuration returns in v1.0.29. v1.0.32 has not yet been tested in a live game. These results cover the tested setup; they do not establish compatibility with every mod or acceptance by every multiplayer server.

| Symptom | Next step |
| --- | --- |
| The game is already running | Close ETS2, start the watchers, then launch a new session. |
| Preparation takes longer after changing mods | Allow the content scan to finish; later launches can reuse the cache. |
| The report lists encrypted definitions | Those definitions were skipped during merging. Check whether the mod provides readable definitions; preparation does not ask for or recover passwords. |
| The database changed after preparation | Prepare a new session. |
| You want a different appearance for a mod | Exit the game and choose truck, bus or car before starting new watchers. |
| Preparation fails, a brand is missing or the game closes | Confirm **v1.0.32**, open the logs and report the mod name and the step that failed. |
| A game or TruckersMP update changes the database format or code signatures | Check for a newer application version and report the error message. |

---

<a id="turkce"></a>

## Türkçe

TruckersMP Mod, yerel ETS2 modlarını TruckersMP ile kullanmak ve oyun içindeki Mod Yöneticisi'ne erişmek için hazırlanmış bir masaüstü başlatıcısıdır.

Kararlı **v1.0.32** sürümünü [Releases](https://github.com/0xdemir/tmp-bypass-mod-manager/releases/latest) bölümünden indir. `TMP.Mod.exe` dosyasını `TMP Mod.exe` adıyla kaydet veya `TMP-Mod-1.0.32.zip` arşivini aç. İkisinde de aynı uygulama bulunur. [Depodaki kopya](TMP%20Mod.exe) da kullanılabilir. Ayrı bir uyumluluk modu kurman gerekmez.

### v1.0.32'de yeni

Save edit ile başka araç modellerinden takılan tanınan orijinal parçalar, desteklenen vanilla tırlarda artık kendi kimlikleriyle gönderiliyor. Önceki sürümler bunları tırın varsayılan parçalarına çevirebiliyor veya çıkarabiliyordu. Parça sırası, tekrarlanan parçalar ve slot bağlantıları korunuyor. Desteklenmeyen yerel modlu araçlar seçilen tır, otobüs veya araba görünümünü kullanmaya devam ediyor.

Oyuncunun bildirdiği Scania S kaydını yeniden işlediğimizde 88 parçanın tamamı korunuyor; önceden 19 parça değiştiriliyor, ikisi çıkarılıyordu. Mevcut veri tabanındaki 26 desteklenen tır modeli üç görünüm seçeneğiyle kontrol edildi. Bu güncellemenin karşı oyuncudaki görüntüsü için canlı doğrulama bekleniyor.

### v1.0.31'de yeni

ZIP tabanlı modlardaki şifreli açıklama dosyaları artık hazırlığı “password required for extraction” hatasıyla durdurmuyor. Hazırlık, adı bilinen ZIP üyelerinde ve açık klasörlerde yalnız `.sii` ve `.sui` tanımlarının içeriğini okuyor. Açıklama, resim ve diğer varlıkların içeriği açılmıyor. İsimsiz HashFS v1 üyelerinin mevcut işlenişi korunuyor.

Bir tanım şifreliyse hazırlık raporuna yazılıyor ve tüm kaynaklarda o dosyanın birleştirmesi atlanıyor. Diğer tanımlar işlenmeye devam ediyor. Bu işlem modun şifresini çözmez veya şifreli tanımlarıyla uyumlu çalışacağını garanti etmez.

### v1.0.17'den bu yana değişenler

- Desteklenmeyen modlu araçların diğer oyunculara görünümü için tır, otobüs ve araba seçenekleri eklendi.
- Test edilen mod kurulumunda eksik bayi markaları ve yanlış marka/araç eşleşmeleri düzeltildi.
- Aracı yapılandırıp bayiye geri dönünce oluşan kapanma düzeltildi. Kullanıcı v1.0.29'da iki yapılandırma/dönüş işlemini arka arkaya sorunsuz tamamladı; sonraki sürümler bu düzeltmeyi korur.
- Hazırlık önbelleği sonraki açılışlarda tekrar kullanılıyor. v1.0.32'de kurulu mod arşiviyle yapılan ölçümde ilk tarama yaklaşık 7 dakika 11 saniye, sonraki hazırlık 23,8 saniye sürdü ve aynı çıktıyı üretti. Süre mod arşivine bağlıdır. Güncelleme veya mod değişikliği yeniden tam tarama gerektirebilir.
- v1.0.30'da araç seçeneklerinin üstüne, oyunun kendi araçlarının kendi marka ve modeliyle göründüğünü açıklayan metin eklendi.

Uyumlu aksesuar veri tabanı (ADB) güncellemeleri otomatik algılanmaya devam eder. Veri tabanı hazırlık sırasında veya sonrasında değişirse yeni oturum hazırla. Veri tabanı biçimi ya da oyun/TruckersMP kod imzaları değişirse uygulama güncellemesi gerekebilir.

### Üç araç görünümü seçeneği nasıl çalışır?

İzleyicileri başlatmadan önce **Karşı tarafta görünen araç** seçimini yap. Bu seçim, desteklenmeyen yerel modlu aracın diğer oyunculara hangi araç olarak gönderileceğini belirler. Sen kendi modunun modelini ve iç mekânını görmeye devam edersin; diğer oyuncular seçtiğin desteklenen aracı görür.

| Uygulamadaki seçenek | Diğer oyuncuların gördüğü araç |
| --- | --- |
| **Tır · Volvo FH16** | Volvo FH16 (`volvo.fh16_2012`) |
| **Otobüs · TruckersMP** | Desteklenen TruckersMP otobüsü (`t16shd`) |
| **Araba · Scout** | Scout / Škoda Superb (`skoda.superb`) |

Örneğin bir araba modunun karşı tarafta Scout görünmesi için **Araba · Scout**, otobüs modunun desteklenen otobüs olarak görünmesi için **Otobüs · TruckersMP** seçebilirsin. Seçim, o oturumdaki desteklenmeyen modlu araçlara uygulanır; her modun türüne göre kendiliğinden değişmez. Seçimi değiştirmek için yeni oturum başlat.

**Oyunun kendi vanilla araçları kendi marka ve modeliyle görünür.** Volvo seçili olsa da vanilla Scania, Scania olarak kalır. TruckersMP'nin zaten tanıdığı araçlar da desteklenen kimliklerini korur. Bu seçim, kısıtlı araç veya parçalara erişim yetkisi vermez; istemci ve sunucu kuralları uygulanmaya devam eder. Uyumluluk, modun tanımlarına ve bağımlılıklarına bağlıdır.

Desteklenen vanilla tırlarda, TruckersMP'nin tanıdığı orijinal parçalar save edit ile farklı bir modele takılsa da parça kimlikleri ve slot bağlantıları korunur. Tanınmayan yerel parçalar için mevcut eşleştirme kuralları uygulanır.

### Gereksinimler

| Bileşen | Gereksinim |
| --- | --- |
| İşletim sistemi | 64-bit Windows |
| Oyun | Kurulu ETS2; test edilen sürüm: **1.61.1.9s** |
| Çok oyunculu | Kurulu resmî TruckersMP başlatıcısı; yerel core sürümü: **0.7.8.3** |
| Yetki | `TMP Mod.exe` yönetici olarak çalıştırılmalı |
| Ek kurulum | Ek çalışma ortamı kurulumu gerekmez |

### Kurulum ve kullanım

1. Yeni oturum hazırlamadan önce ETS2'yi ve eski TMP Mod pencerelerini kapat.
2. `TMP Mod.exe` dosyasını `%APPDATA%\TruckersMP` klasörüne yerleştir.
3. `TMP Mod.exe` dosyasına sağ tıkla, **Yönetici olarak çalıştır** seçeneğini seç ve Windows izin penceresini onayla. Ardından yukarıda açıklanan araç görünümünü seç.
4. **İzleyicileri başlat** düğmesine bas.
5. **OYNA için hazır** durumunu bekle.
6. **TruckersMP’yi aç** düğmesine bas, ardından resmî başlatıcıda **OYNA** seçeneğini kullan.
7. Modlarını ve aracını oyundan seç.

TMP Mod penceresini kapatmak etkin uyarlamayı durdurmaz. Oturumu bitirmek için oyundan çık. **Beklemeyi iptal et**, oyun başlamadan önce beklemeyi iptal eder. Başarısız bir çalıştırmayı incelemek için **Günlükleri aç** düğmesini kullan.

### Antivirüs uyarıları ve izin verme

Antivirüs programın `TMP Mod.exe` dosyasını engeller veya karantinaya alırsa dosyayı bu deponun [Releases](https://github.com/0xdemir/tmp-bypass-mod-manager/releases/latest) sayfasından indirdiğini ve SHA-256 değerinin [Dosya bütünlüğü](#file-integrity--dosya-bütünlüğü) bölümündeki değerle eşleştiğini kontrol et. Bağlantıdaki [VirusTotal raporu önceki v1.0.31 EXE dosyasına aittir](https://www.virustotal.com/gui/file/7068f9e0c52e38e11e0eb06fa68679b0ffb2dcd83113f6094a4d679c7a6dc1d9). v1.0.32'nin hash değeri farklıdır; incelediğin tarama raporunun indirdiğin dosyanın hash değeriyle eşleştiğini kontrol et.

Doğruladığın dosyaya güveniyor ve çalıştırmak istiyorsan antivirüsünün karantina veya koruma geçmişi ekranından bu dosyaya özel izin ver. Antivirüs korumasını açık tut. Rapor, bağlantıdaki hash değerine sahip EXE için geçerlidir; tarama sonuçları zamanla değişebilir ve güvenlik garantisi vermez.

### Kontroller ve sorun giderme

v1.0.32 için 22 Python politika/veri tabanı testi, 14 kamera/içerik okuma testi ve 58 controller testi geçti. Üç görünüm seçeneğinin her birinde, bildirilen 88 parçanın ve özgün nesnelerinin korunması dahil 46 derlenmiş native senaryo geçti. Çapraz model parça kontrolleri 26 desteklenen tır modelinde, 78 model/seçenek birleşiminde başarılı. Bağımsız kod incelemesi ve derlenmiş paket kontrolleri de geçti. Önceki bayi düzeltmesi 19 bayi/işlem test grubundan geçti; kullanıcı v1.0.29'da bayi eşleşmelerini ve iki yapılandırma dönüşünü doğruladı. v1.0.32 henüz canlı oyunda denenmedi. Bu sonuçlar test edilen kurulumu kapsar; tüm modların uyumluluğunu veya her çok oyunculu sunucunun kabulünü doğrulamaz.

| Durum | Yapılacak işlem |
| --- | --- |
| Oyun zaten açık | ETS2'yi kapat, izleyicileri başlat ve yeni bir oyun oturumu aç. |
| Mod değişikliğinden sonra hazırlık uzun sürüyor | İçerik taramasının tamamlanmasını bekle; sonraki açılışlar önbelleği kullanabilir. |
| Raporda şifreli tanımlar var | Bu tanımların birleştirmesi atlandı. Modun okunabilir tanımlar sunup sunmadığını kontrol et; hazırlık şifre istemez veya şifre kurtarmaz. |
| Hazırlıktan sonra veri tabanı değişti | Yeni oturum hazırla. |
| Modun karşı taraftaki görünümünü değiştirmek istiyorsun | Oyundan çık ve yeni izleyicileri başlatmadan önce tır, otobüs veya araba seç. |
| Hazırlık başarısız, marka eksik veya oyun kapanıyor | **v1.0.32** kullandığını kontrol et; günlüklerle birlikte modun adını ve hatanın oluştuğu adımı bildir. |
| Oyun veya TruckersMP güncellemesi veri tabanı biçimini ya da kod imzalarını değiştirdi | Yeni uygulama sürümünü kontrol et ve hata mesajını bildir. |

---

## File integrity / Dosya bütünlüğü

**TruckersMP Mod 1.0.32** · **12,272,640 bytes / bayt**

EXE SHA-256:

~~~text
35f44beb59e903d38ed077baf24d56658eb73dbb7dbb98da3f9b945565199e60
~~~

ZIP SHA-256 (`TMP-Mod-1.0.32.zip`, 12,155,845 bytes / bayt):

~~~text
bca227e4f5c30bd3bb40e7a3d32890fd4a726bedd0869f22e6cbd560888a1ba5
~~~

~~~powershell
Get-FileHash -LiteralPath '.\TMP Mod.exe' -Algorithm SHA256
~~~

**Contact / İletişim:** Discord: **yasindemir**
