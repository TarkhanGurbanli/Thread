# Thread

## 1️⃣ Singletasking nədir?

- Bir CPU-da bir komputer eyni zamanda yalniz bir program execute (icra) ede biler.
- Kompüterdə həmin anda yalnız bir proqramın işə salınması və digər proqramların gözləməsi baş  verir.
- Klassik köhnə sistemlərdə və ya bəzi resurs məhdud sistemlərdə (embedded sistemlər kimi) bu istifadə olunur.

## 2️⃣ Multitasking nədir?

- Bir CPU eyni anda birdən çox proqramı işlədə bilirmiş kimi göstərir.

- Əslində isə bu, context switching (kontekst dəyişimi) prosesi ilə olur:
  - CPU çox kiçik zaman aralıqlarında (millisaniyələr, mikro saniyələr) bir proqramdan digərinə keçir.

- Bu qədər sürətli dəyişdiyi üçün istifadəçi bunu hiss etmir, sanki bütün proqramlar eyni anda işləyirmiş kimi görünür.

- Yəni əsl paralellik yoxdur, amma rəqabətli şəkildə (concurrent) proqramlar növbə ilə icra olunur.

## 3️⃣ Context Switching nədir?

-  context switching goturecek bir programi isledecek sonra cox cox suretli sekilde o biri programa oturecek, her programin oz thread-leri olur, bu sekilde paralel sekilde yox concurrent sekilde isleyecek, yeni threadleri programlar arasinda cox suretli sekilde oturur, bu Multitasking dir.

- Context Switching CPU-nun bir prosesdən digərinə keçməsi prosesidir.
- Hər prosesin öz stack məlumatı, registrləri və vəziyyəti (state) olur.
- CPU bir prosesin işini dayandırıb, onun vəziyyətini yaddaşa yazır və digər prosesi işə salır.
- Bu proses çox sürətli baş verir və istifadəçi bunu hiss etmir.
- Multitasking sistemi bu texnika sayəsində işləyir.

## 4️⃣ Concurrency və Multitasking

- Concurrency nin basqa bir adi Multitasking dir
- Bizim concurrtency-e achieve(nail olmaq ucun) etmeyimiz ucun multiple core-a ehtiyac yoxdur
- Tək nüvəli prosessor da context switching ilə multitasking edə bilər.

**Parallelism (paralel icra) isə fərqlidir:**
- Parallelism üçün ən azı 2 və ya daha çox CPU nüvəsi lazımdır.
- Həqiqi paralellikdə işlər eyni anda müxtəlif nüvələrdə eyni vaxtda görülür.

## 5️⃣ Performance - Paralelism

- Biz multiple core-lar sayesinde tasklari paralel sekilde execute ede bilerik.
- Paralelism sayesinde 1 period erzinde daha cox is gore bilerik

## 6️⃣ Multithreading nədir?

- Multithreading dedikdə, bir proqram daxilində bir neçə thread-in (ipliklərin) eyni vaxtda işləməsi prosesi başa düşülür.
- Hər bir thread proqram daxilində müstəqil icra olunan kiçik bir əməliyyat axınıdır.
- Yəni bir proqram birdən çox iş parçasına bölünür və bu parçalar eyni anda və ya növbə ilə icra olunur.
- Thread-lər eyni proqramın daxilində çalışdıqları üçün həmin proqramın resurslarını paylaşa bilirlər (məsələn, dəyişənlər, obyektlər və s.).

## 7️⃣ Process icinde ne var?

-  Code Segment (Proqramın kodları burada saxlanılır.)
- Data Segment(Global və static dəyişənlər burada yerləşir.)
- Heap(Dynamic olaraq run-time zamanı yaradılan obyekt və məlumatlar burada yerləşir.)
- Stack(Hər thread-in öz Stack-i olur və burada lokal dəyişənlər, funksiya çağırışları, return address-lər saxlanılır.)
- main Thread ve eger yaradilimsa diger threadler

**Process Control Block (PCB - (Prosesə aid idarəetmə məlumatlarını saxlayır)):**
- Process ID (PID)
- Status (running, waiting)
- CPU register-lərinin vəziyyəti
- Prioritet
- Açıq faylların siyahısı
- Scheduling məlumatları

## 8️⃣ Thread icinde ne var?

- Thread id
- Stack ve ya basqa adi ile Stack frame
- Instruction Pointer (Bu ozunde bir sonraki gelecek threadin addresini saxlayir)
 
## 9️⃣ Niye Multithreading? 

**Multithreading-in əsas məqsədləri iki başlıca səbəblə bağlıdır:**
- Responsiveness -> Concurrency
- Performance -> Paralelism
İndi gəlin bu anlayışları 10 və 11-ci başlıqlarda detallı izah edək.

## 🔟 Responsiveness nədir?

Responsiveness — bir proqramın istifadəçinin əmrlərinə və ya hadisələrə nə qədər tez reaksiya verdiyini göstərən anlayışdır.

**Necə işləyir?**

- Multithreading ilə isə:
  - Uzun çəkən iş ayrı bir thread-də görülür.
  - Main thread isə istifadəçidən gələn əmrlərə cavab verməyə davam edir.
  - Bu da proqramın Responsive (həssas və donmayan) işləməsini təmin edir.

**📌 Nəticə:**
Responsiveness → Concurrency
Yəni birdən çox işin eyni vaxtda və ya növbəli şəkildə baş verməsi Concurrency sayəsində proqramın istifadəçiyə cavab vermə sürətini artırır.

## 1️⃣1️⃣ Performance nədir?

Performance — bir proqramın müəyyən işləri nə qədər tez və effektiv icra etməsi deməkdir.

**📌 Necə işləyir?**

- Çoxsaylı və ağır işləri eyni anda fərqli thread-lərə bölüb, fərqli CPU nüvələrində işlətməklə, proqramın icra müddəti xeyli azalır.
- Bu zaman işlər əsl paralel şəkildə görülür və ümumi iş çox daha tez bitir.

**📌 Misal:**
Bir proqram video konvert edərkən:

- Bir thread video-nun səsini işləyir.
- Bir thread görüntünü konvert edir.
- Başqa bir thread isə faylı yazır.

Bu işlər fərqli CPU nüvələrində eyni anda görülə bilər.

**📌 Nəticə:**

Performance → Parallelism
Yəni fərqli CPU nüvələri üzərində eyni anda fərqli işlərin görülməsi Parallelism sayəsində proqramın icra sürətini artırır.

---

## 1️⃣2️⃣ Multithreading-in çıxardığı problemlər və onların həlli

**📌 Shared Mutable State Issues**
(Paylaşılan dəyişkən vəziyyət problemləri)

**Bir neçə thread eyni anda eyni resursa və ya dəyişənə çıxış edəndə bu problemlər yaranır:**

### **`Race Conditions` (Yarış halı):**

- **Problem:** İki və ya daha çox thread eyni dəyişəni eyni anda oxuyub yazanda, nəticə gözlənilməz ola bilər.

- **Həll:**
  - `synchronized` blokları
  - `ReentrantLock`
  - Atomic dəyişənlər (məs. `AtomicInteger`)
  - ya da no shared state dizaynı

 ### Invisible Writes (Görünməyən yazmalar)

- **Problem:** Bir thread-in dəyişdiyi dəyər digər thread tərəfindən vaxtında görünməyə bilər.

- **Həll:**
  - `volatile` açar sözü
  - `synchronized` blokları
  - Memory barrier-lər (JVM səviyyəsində)

### Congestion (Tıxanma)

- **Problem:** Çox sayda thread eyni resursa girməyə çalışanda resurs sıxlığı yaranır və sistem ləngiyir.

- **Həll:**
  - Əlverişli lock strategiyası
  - `ReadWriteLock`
  - `Semaphore`
  - `Thread pool`-lar
 
### Deadlock (Çıxılmaz vəziyyət)

- **Problem:** İki və ya daha çox thread bir-birinin kilidini gözləyir və heç biri işi davam etdirə bilmir.

- **Həll:**
  - Lock sırası (lock ordering)
  - `tryLock()` istifadə etmək
  - `Timeout`-la lock almaq
  - `Deadlock detection` mexanizmi
 
### Nested Monitor Lockout (İç-içə lock bloklanması)

- **Problem:** Bir thread özündə bir neçə lock tutduqda və başqası bu lock-lardan birini almağa çalışanda bloklanıb qalması

- **Həll:**
  - Lock sıralamasını planlaşdırmaq
  - Bir lock içində başqa lock istifadə etməmək

### Starvation (Aclıq vəziyyəti)

- **Problem:** Aşağı prioritetli thread-lər resurs ala bilmir və sonsuz gözləyir
- Həll:
  - Fair lock-lar (`ReentrantLock(true)`)
  - Thread prioritetlərini balanslı bölüşdürmək
 
### Slipped Conditions (Sürüşən vəziyyətlər)

- **Problem:** Thread bir şərti yoxlayıb lock almamış, vəziyyət dəyişir və bu hal gözəgörünməz qalır.

- **Həll:**
  - `synchronized` və ya Lock blokları daxilində şərti yoxlamaq
  - `wait()` / `notify()` mexanizmi ilə dəstəkləmək

### Missed Signals (Qaçırılan siqnallar)

- **Problem:** Bir thread digərini notify() ilə xəbərdar edir, amma xəbərdarlıq ediləcək thread hələ wait()-ə keçməyib.

- Həll:
  - `Condition` obyektləri ilə `await()` və `signal()` istifadə etmək
  - Yaxşı dizayn olunmuş `wait-notify` mexanizmi

**📌 No Shared Mutable State Concurrency**
**(Paylaşılan dəyişən olmadan paralelləşmə modelləri)**
Bu problemlər paylaşılan mutable state olmadıqda demək olar ki, aradan qalxır.

### Separate State Concurrency (Ayrı vəziyyət paralelliyi)**

- Hər thread öz məlumatı ilə işləyir, paylaşma yoxdur.
- Məsələn: hər thread öz obyektini yaradır.

### Functional Parallelism (Funksional paralelizm)

- Immutable dəyişənlər və side-effect olmayan funksiyalarla işləyir.
- Scala, Kotlin, Clojure kimi dillərdə populyardır.

### Parallel Pipelines (Paralel boru xətti icrası)

- İşlər mərhələ-mərhələ paralel axınla ötürülür.
- Hər mərhələ ayrı thread və ya prosesdə işləyir.

---

## 1️⃣2️⃣ ReentrantLock nədir?

- Lock mexanizmidir, `synchronized`-a bənzəyir.
Eyni thread bir lock-u birdən çox dəfə əldə edə bilər və unlock etdikcə tam azad olunur.
**Daha çox əlavə imkanlar təqdim edir:**

- `lock()` — Thread-ə lock almağa icazə verir. Əgər lock alınmayıbsa, gözləyir.
- `unlock()` — Əldə olunan lock-u sərbəst buraxır.
- `tryLock()` — Lock almağa cəhd edir, alınsa true, yoxdursa false qaytarır. Deadlock riskini azaldır.
- `lockInterruptibly()` — Lock alarkən thread interrupt olunsa, gözləməyi dayandırır.
- `newCondition()` — ReentrantLock üçün Condition obyektini yaradır.

**Misal**

```java
ReentrantLock lock = new ReentrantLock();
lock.lock();
try {
    // critical section
} finally {
    lock.unlock();
}
```

### 📌 ReentrantLock(true) nədir?

- Ədalətli (fair) `ReentrantLock`.
- `true` verəndə ilk lock istəyi edən thread, ilk lock-u alır.
- Yəni FIFO (first-in, first-out) prinsipinə əsaslanır.
- Əks halda (default false) — JVM optimallaşdırma üçün bəzən sıralamadan kənar thread-lərə prioritet verə bilər.

```java
ReentrantLock lock = new ReentrantLock(true);
```



