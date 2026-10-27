<div align="center">

![TruckersMP Mod Manager Bypass](assets/truckersmp-mod-banner.png)

# TruckersMP Mod

### TruckersMP Mod Manager Bypass

Local mods and vehicle compatibility for Euro Truck Simulator 2.

Euro Truck Simulator 2 için yerel modlar ve araç uyumluluğu.

![Version](https://img.shields.io/badge/version-1.0.35-27c8bb)
![Platform](https://img.shields.io/badge/platform-Windows_x64-0078d4)
![Distribution](https://img.shields.io/badge/distribution-single_EXE-555555)

**[Download v1.0.35 / v1.0.35 indir](https://github.com/0xdemir/tmp-bypass-mod-manager/releases/download/v1.0.35/TMP.Mod.exe)**

[English](#english) · [Türkçe](#turkce)

</div>

---

<a id="english"></a>

## English

TruckersMP Mod is a desktop launcher for using local ETS2 mods with TruckersMP and accessing the in-game Mod Manager.

Download stable **v1.0.35** from [Releases](https://github.com/0xdemir/tmp-bypass-mod-manager/releases/latest). Save `TMP.Mod.exe` as `TMP Mod.exe`, or extract `TMP-Mod-1.0.35.zip`. Both contain the same application. A [repository copy](TMP%20Mod.exe) is also available. No separate compatibility mod is required.

### New in v1.0.35

- Added a **TR / EN** language selector. Buttons, status messages and dialogs switch immediately; the selected language is saved for the next launch.
- Updated compatibility with the 27 October TruckersMP core update. Fixed preparation stopping with `database global: expected 1 hit, found 0`. The resolver checks the database vector layout and all seven accessory types before accepting the updated image.
- Deleted local mod packages and unsubscribed Workshop items retained in the saved active list no longer stop preparation when their absence can be confirmed. Missing entries are reported; profiles are not edited. Duplicate packages, incomplete installations and an undetected Workshop directory still require attention.
- Added general handling for extra accessory categories belonging to the source vehicle. Unsupported extras can be omitted from the outgoing representation without changing local mod files or saves. Recognized original parts retain their existing handling; missing essentials and ambiguous vehicle roots still reject adaptation.
- Improved game-exit detection and error reporting. An error after adaptation is reported as an interrupted session monitor instead of a preparation failure.

### New in v1.0.34

- Fixed Steam Workshop IDs from saved profile package entries so they resolve to the corresponding Steam item directory.
- Added bounded, rotating local JSONL diagnostics for startup, preparation stages, durations and errors. **Create diagnostic ZIP** asks before exporting and lets you choose where to save it. The bundle includes recent run status/error logs, removes user/profile paths, and excludes profile saves and mod archives. Mod names or Workshop IDs may appear; inspect the ZIP before sharing. It is never uploaded automatically.
- Refined the launcher layout, including clearer status and vehicle-choice cards and separated utility buttons.

Older EXEs cannot gain update notifications remotely. Download v1.0.35 manually once to receive notices about future releases.

### New in v1.0.33

- The saved profile is selected automatically. Preparation reads enabled mods and the required TruckersMP packages, then reuses its cache on later launches.
- You can change enabled mods in the same prepared profile through the in-game Mod Manager. Apply the changes and let the profile finish loading; definitions refresh during that session.
- Mods with vehicle definitions under `/def/vehicle/car/` now use the same mapping as `/def/vehicle/truck/` mods. This fixes the tested “Invalid accessory set detected. Vehicle data not found!” disconnect. Mapping follows part categories rather than rules for individual mod names.
- Added manual console support for time, weather and game speed, plus **0 camera + Ctrl+F9** teleport. Commands run when you enter them; the launcher does not choose values or execute commands automatically.
- Opening the application checks for a newer stable GitHub release. **Güncelleme var** and **Güncellemeyi aç** appear when one is available. The button opens Releases; download and installation remain manual. A failed update check does not block startup.
- Fixed watcher failures when a module disappears during a process query. Earlier dealer and configuration-return fixes are included.

### Original parts and save editing

Known original parts attached from other vehicle models through save editing now keep their identity on supported stock trucks. Earlier versions could replace them with the truck's defaults or omit them. Part order, repeated parts and attachment data are preserved. Unsupported local mod vehicles continue to use the selected truck, bus or car appearance.

Replaying a reported Scania S configuration now preserves all 88 parts; previously, 19 were replaced and two were omitted. Checks cover the 26 supported truck models in the current database with all three appearance choices. Live multiplayer rendering of this update still needs confirmation.

### New in v1.0.31

Encrypted description files in ZIP-based mods no longer stop preparation with a “password required for extraction” error. For ZIP entries and loose files with known names, preparation reads only `.sii` and `.sui` definitions. Descriptions, images and other assets are skipped during content reading. Existing handling for unnamed HashFS v1 entries is unchanged.

If a definition is encrypted, it is recorded in the preparation report and excluded from merging across all sources. Other definitions can still be processed. This does not decrypt the mod or guarantee compatibility with its encrypted definitions.

### What changed since v1.0.17

- Added truck, bus and car choices for how unsupported mod vehicles appear to other players.
- Fixed missing dealer brands and incorrect brand/vehicle associations in the tested mod setup.
- Fixed the crash when returning to the dealer after configuring a vehicle. Two consecutive configuration/return cycles passed the user's live test in v1.0.29; later releases keep that fix.
- Preparation scans the enabled mod selection rather than the entire local mod library. A compiled v1.0.33 preparation with one enabled car mod and a reusable cache took 7.90 seconds. Time depends on the selected mods and cache state.
- v1.0.30 adds an explanation above the vehicle choices: stock vehicles keep their own make and model.

Skipping a deleted package does not restore vehicles or trailers that still depend on it in a save. Restore that mod temporarily, remove its dependent vehicles or trailers in game, and save before deleting it again.

Compatible accessory database (ADB) updates are still detected automatically. If the database changes during or after preparation, prepare a new session. A different database format or changed game/TruckersMP code signatures may require an application update.

### How the three vehicle choices work

Choose **Vehicle other players see** before starting the watchers. This sets the network representation of an unsupported local mod vehicle. You continue to see your own mod's model and interior; other players see the selected supported vehicle.

| Choice in the application | Other players see |
| --- | --- |
| **TRUCK · Volvo FH16** | Volvo FH16 (`volvo.fh16_2012`) |
| **BUS · TruckersMP** | The supported TruckersMP bus (`t16shd`) |
| **CAR · Scout** | Scout / Škoda Superb (`skoda.superb`) |

For example, choose **CAR · Scout** for a car mod to represent it as a Scout, or **BUS · TruckersMP** for a bus mod to represent it as the supported bus. This choice applies to unsupported mod vehicles throughout that session; it does not automatically switch based on the type of each mod. Start a new session to change it.

**Stock ETS2 vehicles keep their own make and model.** A stock Scania stays a Scania even with Volvo selected. Vehicles already recognized by TruckersMP also keep their supported identity. The choice does not grant access to restricted vehicles or parts; client and server rules still apply. Compatibility depends on the mod's definitions and dependencies.

On supported stock trucks, original parts already recognized by TruckersMP keep their identity and attachment data even when save editing places them on a different model. Unknown local parts still follow the existing mapping rules.

### Requirements

| Component | Requirement |
| --- | --- |
| Operating system | 64-bit Windows |
| Game | Installed ETS2; tested build: **1.61.1.9s** |
| Multiplayer | Installed official TruckersMP launcher; local core version: **0.7.9.2** |
| Permissions | Run `TMP Mod.exe` as administrator |
| Extra installation | No additional runtime installation required |

### Install and start

1. Close ETS2 and any older TMP Mod windows before preparing a new session.
2. Place `TMP Mod.exe` in `%APPDATA%\TruckersMP`.
3. Right-click `TMP Mod.exe`, select **Run as administrator** and approve the Windows prompt. Then choose the vehicle appearance described above.
4. Select **TR** or **EN** in the header, then click **Start watchers**.
5. Wait for **Ready for PLAY**.
6. Click **Open TruckersMP**, then press **PLAY / OYNA** in the official TruckersMP launcher.
7. Select your mods and vehicle in the game.

To change enabled mods during play, use the same prepared profile, apply the changes in the in-game Mod Manager and wait for loading to finish. Prepare a new session when switching to another profile.

Closing the TMP Mod window leaves an active adaptation running. Exit the game to end that session. **Cancel waiting** cancels waiting before the game starts. Use **Open logs** to inspect a failed run. The selected language is stored locally in `TMP-Mod-settings.json` and restored on the next launch.

### Manual console commands

Enter commands yourself in the game console.

| Example | Effect |
| --- | --- |
| `g_set_time 12 30` | Sets local time to 12:30 |
| `g_set_weather 1` / `g_set_weather 0` | Starts / stops rain; allow time for the transition |
| `warp 0.8` / `warp 1` | Changes game speed / returns it to normal |
| **0 camera + Ctrl+F9** | Moves the vehicle to the free-camera position |

Console variable handling also covers values such as `g_brake_intensity` and `g_trailer_stability`. The latter retained a test value of `2`; its physical effect was not separately measured. The game's own validation remains, and not every available command has been tested.

### Antivirus alerts and permissions

If your antivirus blocks or quarantines `TMP Mod.exe`, check that you downloaded it from this repository's [Releases](https://github.com/0xdemir/tmp-bypass-mod-manager/releases/latest) page and that its SHA-256 matches the value under [File integrity](#file-integrity). The linked [VirusTotal report covers the previous v1.0.31 EXE](https://www.virustotal.com/gui/file/7068f9e0c52e38e11e0eb06fa68679b0ffb2dcd83113f6094a4d679c7a6dc1d9). v1.0.35 has a different hash; check any scan report against the hash of your downloaded file.

If you trust the verified file and decide to run it, allow that specific file through your antivirus's quarantine or protection history screen. Keep antivirus protection enabled. The report applies to the EXE with the linked hash; scan results can change and do not guarantee safety.

### Checks and troubleshooting

v1.0.35 passed 115 controller tests, 36 launcher/update/language tests, 27 vehicle-policy tests and seven focused core-update regressions. The frozen package check passed for truck, bus and car modes, each with 63 compiled native scenarios. Cached preparation with the current enabled profile completed in 8.38 seconds without accessing the game process. Server entry with the updated core was confirmed without a kick before the language feature was added; the final language build passed package and preparation checks.

Live checks confirmed startup, mod changes in the same profile, time/weather commands and free-camera teleport. With the `/car/` fix, the tested car joined the server without being kicked. Save-edited original parts remain covered by the reported 88-part configuration tests. Remote appearance for each setup still needs a second player's check; these results do not cover every mod.

| Symptom | Next step |
| --- | --- |
| The game is already running | Close ETS2, start the watchers, then launch a new session. |
| Preparation takes longer after changing mods | Allow the content scan to finish; later launches can reuse the cache. |
| The report lists encrypted definitions | Those definitions were skipped during merging. Check whether the mod provides readable definitions; preparation does not ask for or recover passwords. |
| The database changed after preparation | Prepare a new session. |
| You want a different appearance for a mod | Exit the game and choose truck, bus or car before starting new watchers. |
| Preparation fails, a brand is missing or the game closes | Confirm **v1.0.35**, create a diagnostic ZIP, inspect it and share it with the mod name and failing step. |
| A game or TruckersMP update changes the database format or code signatures | Check for a newer application version and report the error message. |

---

<a id="turkce"></a>

## Türkçe

TruckersMP Mod, yerel ETS2 modlarını TruckersMP ile kullanmak ve oyun içindeki Mod Yöneticisi'ne erişmek için hazırlanmış bir masaüstü başlatıcısıdır.

Kararlı **v1.0.35** sürümünü [Releases](https://github.com/0xdemir/tmp-bypass-mod-manager/releases/latest) bölümünden indir. `TMP.Mod.exe` dosyasını `TMP Mod.exe` adıyla kaydet veya `TMP-Mod-1.0.35.zip` arşivini aç. İkisinde de aynı uygulama bulunur. [Depodaki kopya](TMP%20Mod.exe) da kullanılabilir. Ayrı bir uyumluluk modu kurman gerekmez.

### v1.0.35'te yeni

- **TR / EN** dil seçimi eklendi. Düğmeler, durum mesajları ve iletişim pencereleri anında değişir; seçilen dil sonraki açılış için kaydedilir.
- 27 Ekim TruckersMP çekirdek güncellemesine uyumluluk eklendi. Hazırlığı durduran `database global: expected 1 hit, found 0` hatası düzeltildi. Yeni dosya kabul edilmeden önce veritabanının liste yapısı ve yedi aksesuar türü doğrulanıyor.
- Kayıtlı etkin mod listesinde kalan silinmiş yerel paketler ve abonelikten çıkılmış Workshop öğeleri, dosyanın eksik olduğu doğrulanabiliyorsa artık hazırlığı durdurmuyor. Eksik girdiler raporlanıyor; profil düzenlenmiyor. Çift paketler, yarım kurulumlar ve bulunamayan Workshop klasörü ayrıca çözülmeli.
- Kaynak araca ait farklı ek parça klasörleri için genel destek eklendi. Desteklenmeyen ek parçalar, yerel mod dosyaları veya kayıt değiştirilmeden karşıya gönderilen görünümden çıkarılabiliyor. Tanınan orijinal parçaların mevcut işlenişi korunuyor; temel parçaları eksik veya araç kökü belirsiz kurulumlarda uyarlama reddediliyor.
- Oyunun kapanmasını algılama ve hata bildirimi iyileştirildi. Uyarlamadan sonraki hatalar, hazırlık hatası yerine oturum izlemesinin durması olarak gösteriliyor.

### v1.0.34'te yeni

- Kayıtlı profil paketlerindeki Steam Workshop numaraları artık ilgili Steam öğe klasörüne doğru çözülüyor.
- Başlangıç, hazırlık aşamaları, süreler ve hatalar için sınırlı boyutta dönen yerel JSONL günlükleri eklendi. **Tanılama ZIP’i oluştur** dışa aktarmadan önce onay ister ve kaydetme yerini sana seçtirir. Paket son oturumların durum/hata günlüklerini içerir; kullanıcı/profil yollarını ayıklar, profil kayıtlarını ve mod arşivlerini içermez. Mod adları veya Workshop numaraları bulunabilir; paylaşmadan önce ZIP’i incele. Paket otomatik yüklenmez.
- Durum ve araç seçimi kartları netleştirildi; alt işlemlerin düğmeleri birbirinden ayrıldı.

Eski EXE'lere güncelleme bildirimi uzaktan eklenemez. Sonraki sürümlerden haberdar olmak için v1.0.35'ü ilk kez elle indir.

### v1.0.33'te yeni

- Kayıtlı profil otomatik seçiliyor. Hazırlık, etkin modları ve gerekli TruckersMP paketlerini okuyor; sonraki açılışlarda önbelleği kullanıyor.
- Hazırlanan aynı profilde oyun içindeki Mod Yöneticisi'nden etkin modları değiştirebilirsin. Değişiklikleri uygula ve profilin yüklenmesini bekle; tanımlar o oturumda yenilenir.
- Tanımları `/def/vehicle/car/` altında bulunan modlar da `/def/vehicle/truck/` modlarıyla aynı eşleme sistemini kullanıyor. Test edilen “Invalid accessory set detected. Vehicle data not found!” atılması düzeltildi. Eşleme, mod adlarına özel kurallarla değil parça türlerine göre çalışıyor.
- Saat, hava ve oyun hızı için manuel konsol desteği ile **0 kamera + Ctrl+F9** ışınlanması eklendi. Komutlar sen yazdığında çalışır; başlatıcı kendiliğinden değer seçmez veya komut çalıştırmaz.
- Uygulama açıldığında GitHub'da daha yeni bir kararlı sürüm aranıyor. Yeni sürüm varsa **Güncelleme var** bildirimi ve **Güncellemeyi aç** düğmesi gösterilir. Düğme Releases sayfasını açar; indirme ve kurulum elle yapılır. Güncelleme kontrolünün başarısız olması açılışı engellemez.
- Süreç sorgusu sırasında bir modül kaldırıldığında oluşan izleyici hatası düzeltildi. Önceki bayi ve yapılandırmadan dönüş düzeltmeleri de bu sürümde var.

### Orijinal parçalar ve save edit

Save edit ile başka araç modellerinden takılan tanınan orijinal parçalar, desteklenen vanilla tırlarda artık kendi kimlikleriyle gönderiliyor. Önceki sürümler bunları tırın varsayılan parçalarına çevirebiliyor veya çıkarabiliyordu. Parça sırası, tekrarlanan parçalar ve slot bağlantıları korunuyor. Desteklenmeyen yerel modlu araçlar seçilen tır, otobüs veya araba görünümünü kullanmaya devam ediyor.

Oyuncunun bildirdiği Scania S kaydını yeniden işlediğimizde 88 parçanın tamamı korunuyor; önceden 19 parça değiştiriliyor, ikisi çıkarılıyordu. Mevcut veri tabanındaki 26 desteklenen tır modeli üç görünüm seçeneğiyle kontrol edildi. Bu güncellemenin karşı oyuncudaki görüntüsü için canlı doğrulama bekleniyor.

### v1.0.31'de yeni

ZIP tabanlı modlardaki şifreli açıklama dosyaları artık hazırlığı “password required for extraction” hatasıyla durdurmuyor. Hazırlık, adı bilinen ZIP üyelerinde ve açık klasörlerde yalnız `.sii` ve `.sui` tanımlarının içeriğini okuyor. Açıklama, resim ve diğer varlıkların içeriği açılmıyor. İsimsiz HashFS v1 üyelerinin mevcut işlenişi korunuyor.

Bir tanım şifreliyse hazırlık raporuna yazılıyor ve tüm kaynaklarda o dosyanın birleştirmesi atlanıyor. Diğer tanımlar işlenmeye devam ediyor. Bu işlem modun şifresini çözmez veya şifreli tanımlarıyla uyumlu çalışacağını garanti etmez.

### v1.0.17'den bu yana değişenler

- Desteklenmeyen modlu araçların diğer oyunculara görünümü için tır, otobüs ve araba seçenekleri eklendi.
- Test edilen mod kurulumunda eksik bayi markaları ve yanlış marka/araç eşleşmeleri düzeltildi.
- Aracı yapılandırıp bayiye geri dönünce oluşan kapanma düzeltildi. Kullanıcı v1.0.29'da iki yapılandırma/dönüş işlemini arka arkaya sorunsuz tamamladı; sonraki sürümler bu düzeltmeyi korur.
- Hazırlık, tüm yerel mod arşivi yerine etkin mod seçimini tarıyor. Derlenmiş v1.0.33 ile bir araba modu etkinken ve önbellek kullanılabilirken hazırlık 7,90 saniye sürdü. Süre, seçilen modlara ve önbelleğin durumuna bağlıdır.
- v1.0.30'da araç seçeneklerinin üstüne, oyunun kendi araçlarının kendi marka ve modeliyle göründüğünü açıklayan metin eklendi.

Silinen paketin atlanması, kayıt dosyasında o moda bağlı araç veya dorseleri onarmaz. Modu geçici olarak geri yükle, ona bağlı araç veya dorseleri oyundan kaldır ve yeniden silmeden önce kaydet.

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
| Çok oyunculu | Kurulu resmî TruckersMP başlatıcısı; yerel core sürümü: **0.7.9.2** |
| Yetki | `TMP Mod.exe` yönetici olarak çalıştırılmalı |
| Ek kurulum | Ek çalışma ortamı kurulumu gerekmez |

### Kurulum ve kullanım

1. Yeni oturum hazırlamadan önce ETS2'yi ve eski TMP Mod pencerelerini kapat.
2. `TMP Mod.exe` dosyasını `%APPDATA%\TruckersMP` klasörüne yerleştir.
3. `TMP Mod.exe` dosyasına sağ tıkla, **Yönetici olarak çalıştır** seçeneğini seç ve Windows izin penceresini onayla. Ardından yukarıda açıklanan araç görünümünü seç.
4. Üst bölümden **TR** veya **EN** seç, ardından **İzleyicileri başlat** düğmesine bas.
5. **OYNA için hazır** durumunu bekle.
6. **TruckersMP’yi aç** düğmesine bas, ardından resmî başlatıcıda **OYNA** seçeneğini kullan.
7. Modlarını ve aracını oyundan seç.

Oyun sırasında etkin modları değiştirmek için hazırlanan aynı profili kullan, oyun içindeki Mod Yöneticisi'nde değişiklikleri uygula ve yüklemenin tamamlanmasını bekle. Başka profile geçerken yeni oturum hazırla.

TMP Mod penceresini kapatmak etkin uyarlamayı durdurmaz. Oturumu bitirmek için oyundan çık. **Beklemeyi iptal et**, oyun başlamadan önce beklemeyi iptal eder. Başarısız bir çalıştırmayı incelemek için **Günlükleri aç** düğmesini kullan. Dil seçimi yerel `TMP-Mod-settings.json` dosyasında saklanır ve sonraki açılışta geri yüklenir.

### Manuel konsol komutları

Komutları oyun konsoluna kendin yaz.

| Örnek | Etkisi |
| --- | --- |
| `g_set_time 12 30` | Yerel saati 12:30 yapar |
| `g_set_weather 1` / `g_set_weather 0` | Yağmuru başlatır / durdurur; geçiş için bir süre bekle |
| `warp 0.8` / `warp 1` | Oyun hızını değiştirir / normale döndürür |
| **0 kamera + Ctrl+F9** | Aracı serbest kameranın bulunduğu yere taşır |

Konsol değişkenlerinin işlenmesi `g_brake_intensity` ve `g_trailer_stability` gibi değerleri de kapsar. Son komutta denenen `2` değeri korundu; fizik üzerindeki etkisi ayrıca ölçülmedi. Oyunun kendi doğrulaması korunur; mevcut komutların tamamı test edilmiş değildir.

### Antivirüs uyarıları ve izin verme

Antivirüs programın `TMP Mod.exe` dosyasını engeller veya karantinaya alırsa dosyayı bu deponun [Releases](https://github.com/0xdemir/tmp-bypass-mod-manager/releases/latest) sayfasından indirdiğini ve SHA-256 değerinin [Dosya bütünlüğü](#file-integrity) bölümündeki değerle eşleştiğini kontrol et. Bağlantıdaki [VirusTotal raporu önceki v1.0.31 EXE dosyasına aittir](https://www.virustotal.com/gui/file/7068f9e0c52e38e11e0eb06fa68679b0ffb2dcd83113f6094a4d679c7a6dc1d9). v1.0.35'ün hash değeri farklıdır; incelediğin tarama raporunun indirdiğin dosyanın hash değeriyle eşleştiğini kontrol et.

Doğruladığın dosyaya güveniyor ve çalıştırmak istiyorsan antivirüsünün karantina veya koruma geçmişi ekranından bu dosyaya özel izin ver. Antivirüs korumasını açık tut. Rapor, bağlantıdaki hash değerine sahip EXE için geçerlidir; tarama sonuçları zamanla değişebilir ve güvenlik garantisi vermez.

### Kontroller ve sorun giderme

v1.0.35 için 115 controller testi, 36 başlatıcı/güncelleme/dil testi, 27 araç politikası testi ve yedi çekirdek güncelleme testi geçti. Dondurulmuş paket kontrolü tır, otobüs ve araba seçeneklerinin her birinde 63 derlenmiş native senaryoyla başarılı. Mevcut etkin profille önbellekli hazırlık, oyun sürecine erişmeden 8,38 saniyede tamamlandı. Dil özelliği eklenmeden önce yeni çekirdekle sunucuya atılmadan giriş doğrulandı; son dil eklenen derleme paket ve hazırlık kontrollerini geçti.

Canlı testlerde başlangıç, aynı profilde mod değiştirme, saat/hava komutları ve serbest kamera ışınlanması doğrulandı. `/car/` düzeltmesinden sonra denenen araba sunucuya atılmadan girdi. Save edit ile takılan orijinal parçalar, bildirilen 88 parçalık kurulumun testleriyle korunuyor. Her kurulumun karşı oyuncudaki görünümü için ikinci oyuncuyla kontrol gerekir; bu sonuçlar tüm modları kapsamaz.

| Durum | Yapılacak işlem |
| --- | --- |
| Oyun zaten açık | ETS2'yi kapat, izleyicileri başlat ve yeni bir oyun oturumu aç. |
| Mod değişikliğinden sonra hazırlık uzun sürüyor | İçerik taramasının tamamlanmasını bekle; sonraki açılışlar önbelleği kullanabilir. |
| Raporda şifreli tanımlar var | Bu tanımların birleştirmesi atlandı. Modun okunabilir tanımlar sunup sunmadığını kontrol et; hazırlık şifre istemez veya şifre kurtarmaz. |
| Hazırlıktan sonra veri tabanı değişti | Yeni oturum hazırla. |
| Modun karşı taraftaki görünümünü değiştirmek istiyorsun | Oyundan çık ve yeni izleyicileri başlatmadan önce tır, otobüs veya araba seç. |
| Hazırlık başarısız, marka eksik veya oyun kapanıyor | **v1.0.35** kullandığını kontrol et; Tanılama ZIP’i oluştur, içeriğini incele ve mod adıyla hatanın oluştuğu adımı paylaş. |
| Oyun veya TruckersMP güncellemesi veri tabanı biçimini ya da kod imzalarını değiştirdi | Yeni uygulama sürümünü kontrol et ve hata mesajını bildir. |

---

<a id="file-integrity"></a>

## File integrity / Dosya bütünlüğü

**TruckersMP Mod 1.0.35** · **13,192,704 bytes / bayt**

EXE SHA-256:

~~~text
9ab7a6976123894396b7bb9d3efda34b256288c81a69deca2795deceac7f2cef
~~~

ZIP SHA-256 (`TMP-Mod-1.0.35.zip`, 13,078,190 bytes / bayt):

~~~text
7b4cb92c5dd485d44648d7d4e66586c489ca074bae6efdacd4b129844a84fbdc
~~~

~~~powershell
Get-FileHash -LiteralPath '.\TMP Mod.exe' -Algorithm SHA256
~~~

**Contact / İletişim:** Discord: **yasindemir**
