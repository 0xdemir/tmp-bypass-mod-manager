<div align="center">

![TruckersMP Mod Manager Bypass](assets/truckersmp-mod-banner.png)

# TruckersMP Mod

### TruckersMP Mod Manager Bypass

Local mods and vehicle compatibility for Euro Truck Simulator 2.

Euro Truck Simulator 2 için yerel modlar ve araç uyumluluğu.

![Version](https://img.shields.io/badge/version-1.0.38-27c8bb)
![Platform](https://img.shields.io/badge/platform-Windows_x64-0078d4)
![Distribution](https://img.shields.io/badge/distribution-single_EXE-555555)

**[Download v1.0.38 / v1.0.38 indir](https://github.com/0xdemir/tmp-bypass-mod-manager/releases/download/v1.0.38/TMP.Mod.exe)**

[English](#english) · [Türkçe](#turkce)

</div>

---

<a id="english"></a>

## English

TruckersMP Mod is a desktop launcher for using local ETS2 mods with TruckersMP and accessing the in-game Mod Manager.

Download stable **v1.0.38** from [Releases](https://github.com/0xdemir/tmp-bypass-mod-manager/releases/latest). Save `TMP.Mod.exe` as `TMP Mod.exe`, or extract `TMP-Mod-1.0.38.zip`. Both contain the same application. A [repository copy](TMP%20Mod.exe) is also available. No separate compatibility mod is required.

### New in v1.0.38

- Improved how original parts moved between vanilla vehicles with save editing appear to other players.
- Uses **367,447 verified visual mappings** for **22,707 eligible parts** extracted from the game archives. Matching is based on each part's actual **PMD model identity**, not just its filename.
- Known parts without a verified visual equivalent are preserved; paint, wheels, part order and attachment data are not changed.
- Two-player live visual verification and live-server acceptance have not been established. Correct rendering is not guaranteed for every part combination.

### New in v1.0.37

- Updated compatibility for **ETS2 1.62.1.0s** and **TruckersMP core 0.7.10.0**. The manager/core targets and their cross-validation were updated, fixing the `manager_handler` startup failure after the TruckersMP update.
- The live check passed startup and reached **PLAY / Sür**. Live-server acceptance has not been verified.
- The TR / EN interface, three vehicle appearance choices and earlier compatibility fixes are retained.

A separate live ETS2 exit on 8 November at 03:44 occurred while loading a `.tobj`: `p3_alloc` failed to allocate **11,184,868 bytes (10.666721 MiB)** with alignment **0**. The evidence supports memory pressure. This release does not claim a permanent fix for that crash or for the earlier `std::bad_alloc` failure.

### New in v1.0.36

- Damaged core-map caches are rebuilt from the installed TruckersMP DLL. Cache entries also have to match the actual code bytes and image layout; a cache write failure no longer discards a successful resolution.
- Preparation no longer reports a failure just because its elevated worker takes more than 60 seconds. It waits for the worker to finish and uses its exit result.
- A CRC-damaged definition in a ZIP mod no longer stops the entire merge plan. The affected definition is reported and excluded from merging across sources; unrelated readable definitions can still be processed.
- Diagnostic records stay within 32 KiB even with nested details. Diagnostic export reads only the bounded tail of each log, so large logs do not have to be loaded entirely into memory.

These fixes retain the TR / EN interface and the three vehicle appearance choices. This release does not claim to fix loading-screen crashes caused by failed memory allocation (`std::bad_alloc`).

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

Older EXEs cannot gain update notifications remotely. Download v1.0.38 manually once to receive notices about future releases.

### New in v1.0.33

- The saved profile is selected automatically. Preparation reads enabled mods and the required TruckersMP packages, then reuses its cache on later launches.
- You can change enabled mods in the same prepared profile through the in-game Mod Manager. Apply the changes and let the profile finish loading; definitions refresh during that session.
- Mods with vehicle definitions under `/def/vehicle/car/` now use the same mapping as `/def/vehicle/truck/` mods. This fixes the tested “Invalid accessory set detected. Vehicle data not found!” disconnect. Mapping follows part categories rather than rules for individual mod names.
- Added manual console support for time, weather and game speed, plus **0 camera + Ctrl+F9** teleport. Commands run when you enter them; the launcher does not choose values or execute commands automatically.
- Opening the application checks for a newer stable GitHub release. **Güncelleme var** and **Güncellemeyi aç** appear when one is available. The button opens Releases; download and installation remain manual. A failed update check does not block startup.
- Fixed watcher failures when a module disappears during a process query. Earlier dealer and configuration-return fixes are included.

### Original parts and save editing

On supported stock trucks, an original part from another vanilla model is mapped only when a part on the target vehicle is verified to use the same PMD model in the same category. Same-named parts with different PMD models are not treated as equivalents. Known parts without a verified equivalent are preserved. Part order, repeated parts and attachment data are retained; unsupported local mod vehicles continue to use the selected truck, bus or car appearance.

The current table contains 367,447 mappings for 22,707 eligible parts, including 285 unique mappings with different filenames. Tests cover all 26 supported truck models and the three appearance choices. Two-player live visual confirmation is still required for specific combinations.

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
| Game | Installed ETS2; tested build: **1.62.1.0s** |
| Multiplayer | Installed official TruckersMP launcher; local core version: **0.7.10.0** |
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

If your antivirus blocks or quarantines `TMP Mod.exe`, check that you downloaded it from this repository's [Releases](https://github.com/0xdemir/tmp-bypass-mod-manager/releases/latest) page and that its SHA-256 matches the value under [File integrity](#file-integrity). The linked [VirusTotal report covers the previous v1.0.31 EXE](https://www.virustotal.com/gui/file/7068f9e0c52e38e11e0eb06fa68679b0ffb2dcd83113f6094a4d679c7a6dc1d9). v1.0.38 has a different hash; check any scan report against the hash of your downloaded file.

If you trust the verified file and decide to run it, allow that specific file through your antivirus's quarantine or protection history screen. Keep antivirus protection enabled. The report applies to the EXE with the linked hash; scan results can change and do not guarantee safety.

### Checks and troubleshooting

The update passed 145/145 controller/core tests, 39/39 launcher/language/update tests and 30/30 visual-projection tests. The native policy passed 68 cases for each of truck, bus and car. The frozen 1.0.38 package passed payload validation and all three `--prepare-only` checks without starting the game or accessing a game process. Two-player live visual verification and live-server acceptance remain unverified; these results do not establish a fix for the observed game memory-allocation crashes.

Earlier live checks confirmed startup, mod changes in the same profile, time/weather commands and free-camera teleport. With the `/car/` fix, the tested car joined the server without being kicked. Save-edited original parts remain covered by the reported 88-part configuration tests. Remote appearance for each setup still needs a second player's check; these results do not cover every mod.

| Symptom | Next step |
| --- | --- |
| Loading closes the game with `std::bad_alloc` / `bad allocation` | A memory allocation failed. Free memory from unneeded applications and retry with the same setup. If it repeats, share diagnostics and the latest game crash log. |
| Loading exits with `p3_alloc` while reading a `.tobj` | A game texture allocation failed. Reduce memory use and retry with the same setup. The 8 November event requested 11,184,868 bytes; this release does not claim to fix that allocation failure. |
| The game is already running | Close ETS2, start the watchers, then launch a new session. |
| Preparation takes longer after changing mods | Allow the content scan to finish; later launches can reuse the cache. |
| The report lists encrypted definitions | Those definitions were skipped during merging. Check whether the mod provides readable definitions; preparation does not ask for or recover passwords. |
| The database changed after preparation | Prepare a new session. |
| You want a different appearance for a mod | Exit the game and choose truck, bus or car before starting new watchers. |
| Preparation fails, a brand is missing or the game closes | Confirm **v1.0.38**, create a diagnostic ZIP, inspect it and share it with the mod name and failing step. |
| A game or TruckersMP update changes the database format or code signatures | Check for a newer application version and report the error message. |

---

<a id="turkce"></a>

## Türkçe

TruckersMP Mod, yerel ETS2 modlarını TruckersMP ile kullanmak ve oyun içindeki Mod Yöneticisi'ne erişmek için hazırlanmış bir masaüstü başlatıcısıdır.

Kararlı **v1.0.38** sürümünü [Releases](https://github.com/0xdemir/tmp-bypass-mod-manager/releases/latest) bölümünden indir. `TMP.Mod.exe` dosyasını `TMP Mod.exe` adıyla kaydet veya `TMP-Mod-1.0.38.zip` arşivini aç. İkisinde de aynı uygulama bulunur. [Depodaki kopya](TMP%20Mod.exe) da kullanılabilir. Ayrı bir uyumluluk modu kurman gerekmez.

### v1.0.38'de yeni

- Vanilla araçlar arasında save edit ile takılan orijinal parçaların karşı oyuncudaki görünümü iyileştirildi.
- Oyun arşivlerinden çıkarılan **22.707 uygun parça** için **367.447 doğrulanmış görsel eşleme** kullanılıyor. Eşleme yalnız dosya adına göre değil, parçanın kullandığı gerçek **PMD model kimliğine** göre yapılıyor.
- Görsel karşılığı doğrulanamayan veya bulunamayan bilinen parçalar korunuyor; boya, tekerlek, parça sırası ve ek nesne verileri değiştirilmiyor.
- İki oyunculu canlı görsel doğrulama ve canlı sunucu kabulü henüz doğrulanmadı. Her parça kombinasyonunun doğru görüneceği garanti edilmiyor.

### v1.0.37'de yeni

- **ETS2 1.62.1.0s** ve **TruckersMP core 0.7.10.0** uyumluluğu güncellendi. Manager/core hedefleri ve çapraz doğrulamaları yenilendi; TruckersMP güncellemesinden sonra oluşan `manager_handler` başlangıç hatası düzeltildi.
- Canlı kontrolde başlangıç aşaması geçildi ve **PLAY / Sür** aşamasına ulaşıldı. Canlı sunucu kabulü doğrulanmadı.
- TR / EN arayüz, üç araç görünümü seçeneği ve önceki uyumluluk düzeltmeleri korunuyor.

8 Kasım 03:44'teki ayrı canlı ETS2 kapanması, `.tobj` yüklenirken `p3_alloc` işleminin hizalama **0** ile **11.184.868 bayt (10,666721 MiB)** ayıramaması sonucu oluştu. Kanıtlar bellek baskısını destekliyor. Bu sürüm, bu çökmeyi veya önceki `std::bad_alloc` hatasını kalıcı olarak giderdiği iddiasını taşımıyor.

### v1.0.36'da yeni

- Bozuk çekirdek eşleme önbelleği, kurulu TruckersMP DLL dosyasından yeniden oluşturuluyor. Önbellekteki kayıtlar gerçek kod baytları ve dosya yerleşimiyle de doğrulanıyor; önbelleğe yazılamaması başarılı çözümlemeyi iptal etmiyor.
- Yönetici yetkili hazırlık işlemi 60 saniyeyi aşınca artık yanlışlıkla başarısız sayılmıyor. İşlemin bitmesi bekleniyor ve gerçek çıkış sonucu kullanılıyor.
- ZIP modundaki CRC hatalı bir tanım artık bütün birleştirme planını durdurmuyor. Sorunlu tanım raporlanıp tüm kaynaklarda birleştirme dışında tutuluyor; diğer okunabilir tanımlar işlenebiliyor.
- İç içe ayrıntılar içeren tanılama kayıtları da 32 KiB sınırında kalıyor. Tanılama ZIP'i hazırlanırken büyük günlüklerin tamamı yerine yalnız sınırlı son bölümleri okunuyor.

TR / EN arayüz ve üç araç görünümü seçeneği korunuyor. Bu sürüm, bellek ayırma hatasından (`std::bad_alloc`) kaynaklanan yükleme ekranı çökmelerini giderdiği iddiasını taşımıyor.

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

Eski EXE'lere güncelleme bildirimi uzaktan eklenemez. Sonraki sürümlerden haberdar olmak için v1.0.38'yi ilk kez elle indir.

### v1.0.33'te yeni

- Kayıtlı profil otomatik seçiliyor. Hazırlık, etkin modları ve gerekli TruckersMP paketlerini okuyor; sonraki açılışlarda önbelleği kullanıyor.
- Hazırlanan aynı profilde oyun içindeki Mod Yöneticisi'nden etkin modları değiştirebilirsin. Değişiklikleri uygula ve profilin yüklenmesini bekle; tanımlar o oturumda yenilenir.
- Tanımları `/def/vehicle/car/` altında bulunan modlar da `/def/vehicle/truck/` modlarıyla aynı eşleme sistemini kullanıyor. Test edilen “Invalid accessory set detected. Vehicle data not found!” atılması düzeltildi. Eşleme, mod adlarına özel kurallarla değil parça türlerine göre çalışıyor.
- Saat, hava ve oyun hızı için manuel konsol desteği ile **0 kamera + Ctrl+F9** ışınlanması eklendi. Komutlar sen yazdığında çalışır; başlatıcı kendiliğinden değer seçmez veya komut çalıştırmaz.
- Uygulama açıldığında GitHub'da daha yeni bir kararlı sürüm aranıyor. Yeni sürüm varsa **Güncelleme var** bildirimi ve **Güncellemeyi aç** düğmesi gösterilir. Düğme Releases sayfasını açar; indirme ve kurulum elle yapılır. Güncelleme kontrolünün başarısız olması açılışı engellemez.
- Süreç sorgusu sırasında bir modül kaldırıldığında oluşan izleyici hatası düzeltildi. Önceki bayi ve yapılandırmadan dönüş düzeltmeleri de bu sürümde var.

### Orijinal parçalar ve save edit

Desteklenen vanilla tırlarda, başka bir vanilla modelden takılan orijinal parça yalnız hedef araçtaki bir parçanın aynı kategoride aynı PMD modelini kullandığı doğrulanırsa eşleniyor. Dosya adı aynı olsa bile PMD modeli farklı parçalar eşdeğer sayılmıyor. Doğrulanmış karşılığı olmayan bilinen parçalar korunuyor. Parça sırası, tekrarlanan parçalar ve slot bağlantıları korunuyor; desteklenmeyen yerel modlu araçlar seçilen tır, otobüs veya araba görünümünü kullanmaya devam ediyor.

Geçerli tabloda 22.707 uygun parça için 367.447 eşleme bulunuyor; bunların 285'i farklı dosya adları arasında benzersiz eşleme. Testler mevcut veri tabanındaki 26 desteklenen tır modelini ve üç görünüm seçeneğini kapsıyor. Belirli kombinasyonların karşı oyuncudaki görüntüsü için iki oyunculu canlı doğrulama gerekiyor.

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
| Oyun | Kurulu ETS2; test edilen sürüm: **1.62.1.0s** |
| Çok oyunculu | Kurulu resmî TruckersMP başlatıcısı; yerel core sürümü: **0.7.10.0** |
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

Antivirüs programın `TMP Mod.exe` dosyasını engeller veya karantinaya alırsa dosyayı bu deponun [Releases](https://github.com/0xdemir/tmp-bypass-mod-manager/releases/latest) sayfasından indirdiğini ve SHA-256 değerinin [Dosya bütünlüğü](#file-integrity) bölümündeki değerle eşleştiğini kontrol et. Bağlantıdaki [VirusTotal raporu önceki v1.0.31 EXE dosyasına aittir](https://www.virustotal.com/gui/file/7068f9e0c52e38e11e0eb06fa68679b0ffb2dcd83113f6094a4d679c7a6dc1d9). v1.0.38'nin hash değeri farklıdır; incelediğin tarama raporunun indirdiğin dosyanın hash değeriyle eşleştiğini kontrol et.

Doğruladığın dosyaya güveniyor ve çalıştırmak istiyorsan antivirüsünün karantina veya koruma geçmişi ekranından bu dosyaya özel izin ver. Antivirüs korumasını açık tut. Rapor, bağlantıdaki hash değerine sahip EXE için geçerlidir; tarama sonuçları zamanla değişebilir ve güvenlik garantisi vermez.

### Kontroller ve sorun giderme

Güncelleme 145/145 controller/core testini, 39/39 başlatıcı/dil/güncelleme testini ve 30/30 görsel projeksiyon testini geçti. Native politika tır, otobüs ve araba seçimlerinin her biri için 68 vakayı geçti. Derlenmiş 1.0.38 paketi bütünlük doğrulamasını ve üç `--prepare-only` kontrolünü oyunu başlatmadan veya oyun sürecine erişmeden geçti. İki oyunculu canlı görsel doğrulama ve canlı sunucu kabulü henüz doğrulanmadı; bu sonuçlar, gözlenen oyun bellek ayırma çökmelerinin giderildiğini göstermez.

Önceki canlı testlerde başlangıç, aynı profilde mod değiştirme, saat/hava komutları ve serbest kamera ışınlanması doğrulandı. `/car/` düzeltmesinden sonra denenen araba sunucuya atılmadan girdi. Save edit ile takılan orijinal parçalar, bildirilen 88 parçalık kurulumun testleriyle korunuyor. Her kurulumun karşı oyuncudaki görünümü için ikinci oyuncuyla kontrol gerekir; bu sonuçlar tüm modları kapsamaz.

| Durum | Yapılacak işlem |
| --- | --- |
| Yüklemede `std::bad_alloc` / `bad allocation` ile kapanıyor | Bellek ayırma başarısız oldu. Gereksiz uygulamaları kapatıp aynı kurulumla tekrar dene. Tekrarlarsa tanılama paketiyle son oyun çökme günlüğünü paylaş. |
| `.tobj` okunurken `p3_alloc` ile kapanıyor | Oyunun doku belleği ayırması başarısız oldu. Bellek kullanımını azaltıp aynı kurulumla tekrar dene. 8 Kasım olayında 11.184.868 bayt istenmişti; bu sürüm söz konusu ayırma hatasını giderdiğini iddia etmiyor. |
| Oyun zaten açık | ETS2'yi kapat, izleyicileri başlat ve yeni bir oyun oturumu aç. |
| Mod değişikliğinden sonra hazırlık uzun sürüyor | İçerik taramasının tamamlanmasını bekle; sonraki açılışlar önbelleği kullanabilir. |
| Raporda şifreli tanımlar var | Bu tanımların birleştirmesi atlandı. Modun okunabilir tanımlar sunup sunmadığını kontrol et; hazırlık şifre istemez veya şifre kurtarmaz. |
| Hazırlıktan sonra veri tabanı değişti | Yeni oturum hazırla. |
| Modun karşı taraftaki görünümünü değiştirmek istiyorsun | Oyundan çık ve yeni izleyicileri başlatmadan önce tır, otobüs veya araba seç. |
| Hazırlık başarısız, marka eksik veya oyun kapanıyor | **v1.0.38** kullandığını kontrol et; Tanılama ZIP’i oluştur, içeriğini incele ve mod adıyla hatanın oluştuğu adımı paylaş. |
| Oyun veya TruckersMP güncellemesi veri tabanı biçimini ya da kod imzalarını değiştirdi | Yeni uygulama sürümünü kontrol et ve hata mesajını bildir. |

---

<a id="file-integrity"></a>

## File integrity / Dosya bütünlüğü

**TruckersMP Mod 1.0.38** · **15,308,800 bytes / bayt**

EXE SHA-256:

~~~text
8f80a527d122e5a40afccd05941f6757a94b6f0c3e1be60c64cedec11bc38a1a
~~~

ZIP SHA-256 (`TMP-Mod-1.0.38.zip`, 15,123,009 bytes / bayt):

~~~text
cbd5408a7bddee05d5a958b667560bb132e428ffbf806d056c2ac2266ade2676
~~~

~~~powershell
Get-FileHash -LiteralPath '.\TMP Mod.exe' -Algorithm SHA256
~~~

**Contact / İletişim:** Discord: **yasindemir**
