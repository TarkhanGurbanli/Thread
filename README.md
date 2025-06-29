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

## 1️⃣3️⃣ volatile nədir?

- Java keyword-dür.
- Bir dəyişənə `volatile` desək, o hər dəfə oxunanda və yazılanda birbaşa əsas yaddaşdan oxunur və yazılır.
- CPU cache-lərdə saxlanmır, bu da thread-lər arasında görünməyən yazmaları həll edir.
- Sinxronizasiya təmin etmir, sadəcə visibility problemi aradan qalxır.

**Misal:**

```java
volatile boolean flag = true;
```

## 1️⃣4️⃣ Memory Barrier nədir?

- CPU və JVM-in təlimatları icra etmə ardıcıllığını və cache sinxronizasiyasını tənzimləyən mexanizmdir.
- `volatile` və `synchronized` kimi mexanizmlər memory barrier əmrləri qoyur:
  - Yazma barrier
  - Oxuma barrier
- Bu sayədə CPU əmrləri yenidən düzəltmədən icra edir və dəyişənlər dərhal əsas yaddaşda görünür. 

## 1️⃣5️⃣ synchronized nədir?

- Java-da ən klassik sinxronizasiya mexanizmidir.
- Bir thread-in müəyyən kod hissəsinə daxil olarkən digərlərinin girməsini qadağan edir.
- Monitor lock istifadə edir.
- Yəni həmin obyektə ya class, ya obyekt səviyyəsində kilid qoyur.

**Misal:**
```java
synchronized (this) {
    // critical section
}
```

## 1️⃣6️⃣ ReadWriteLock nədir?

- Oxuma və yazma əməliyyatlarını fərqli idarə edən lock mexanizmi.
- Eyni anda bir neçə thread oxuya bilər, amma yazı zamanı digər thread-lər gözləyir.
- Yazı varsa, heç kim oxuya bilmir.

**Misal:**

```java
ReadWriteLock lock = new ReentrantReadWriteLock();
lock.readLock().lock();
// oxuma əməliyyatı
lock.readLock().unlock();
```

## 1️⃣7️⃣ Semaphore nədir?

- İcazə mexanizmi.
- Məlum sayda thread-in eyni anda müəyyən hissəyə girməsinə icazə verir.
- İcazə sayı bitəndə digər thread-lər gözləyir.
- Məsələn, 3 icazə varsa, 3 thread daxil ola bilər, qalanlar gözləyir.

**Misal:**

```java
Semaphore semaphore = new Semaphore(3);
semaphore.acquire();
// iş
semaphore.release();
```

## 1️⃣8️⃣ Thread pool-lar nədir?

- Hazır və idarə olunan thread-lər toplusudur.
- Thread yaratmaq və məhv etmək overhead-inin qarşısını alır.
- Sistem yüklənməsini balanslaşdırır.
- Java-da `ExecutorService` ilə idarə olunur.

**Misal:**

```java
ExecutorService pool = Executors.newFixedThreadPool(5);
pool.execute(() -> System.out.println("Hello"));
```

## 1️⃣9️⃣ wait() / notify() nədir?

- Java-da obyekt səviyyəsində sinxronizasiya üçün istifadə olunur.
- `wait()` → thread-in gözləməsini təmin edir.
- `notify()` → gözləyən thread-lərdən birini oyadır.
- `notifyAll()` → hamısını oyadır.
- Yalnız `synchronized` blok içində işləyir.

**Misal:**

```java
synchronized (lock) {
    lock.wait();
    lock.notify();
}
```

## 2️⃣0️⃣ Condition nədir?

- `ReentrantLock` ilə əvəzolunmuş `wait()` / `notify()` mexanizmi.
- **Daha çox funksionallıq təqdim edir:**
  - `await()`
  - `signal()`
  - `signalAll()`

**Misal:**

```java
Condition condition = lock.newCondition();
lock.lock();
try {
    condition.await();
    condition.signal();
} finally {
    lock.unlock();
}
```

## 📌 Java Concurrency Alətləri və Onların İşi

### 🔒 ReentrantLock
- `lock()` — Thread-ə lock almağa icazə verir. Əgər lock alınmayıbsa, gözləyir.
- `unlock()` — Əldə olunan lock-u sərbəst buraxır.
- `tryLock()` — Lock almağa cəhd edir, alınsa true, yoxdursa false qaytarır. `Deadlock` riskini azaldır.
- `lockInterruptibly()` — Lock alarkən thread interrupt olunsa, gözləməyi dayandırır.
- `newCondition()` — `ReentrantLock` üçün `Condition` obyektini yaradır.

### 🔒 ReentrantLock(true)
**`ReentrantLock(boolean fair)` — Ədalətli (fair) rejimdə lock yaradır. `true` verilsə, lock-lar ilk istəyənə verilir (`FIFO`).**

### 🔑 volatile
- Dəyişənin yaddaşdan oxunub, yazılmasını birbaşa əsas yaddaşda edir. `Visibility` problemini həll edir, amma sinxronizasiya (mutual exclusion) təmin etmir.

### 📏 Memory Barrier
- Oxuma və yazma əmrlərinin CPU və JVM səviyyəsində ardıcıllığını və görünməsini təmin edir.
- `volatile`, `synchronized` və Lock istifadə edəndə memory barrier-lər avtomatik əlavə olunur.

### 🔒 synchronized
- Bir blok və ya metodun eyni anda yalnız bir thread tərəfindən icra olunmasını təmin edir.
- Monitor lock-la işləyir.
- `wait()`, `notify()`, `notifyAll()` yalnız synchronized blok içində çağırıla bilər.

### 📚 ReadWriteLock
- `readLock()` — Oxuma üçün lock verir. Bir neçə thread eyni anda oxuya bilər.
- `writeLock()` — Yazma üçün lock verir. Yalnız bir thread yaza bilər, olanda başqaları gözləyir.

### 🚥 Semaphore
- `acquire()` — İcazə alır. Say varsa icazə verir, yoxdursa gözləyir.
- `release()` — İcazəni geri qaytarır, gözləyən thread varsa oyadır.
- `availablePermits()` — Hal-hazırda neçə icazə olduğunu qaytarır.
- `tryAcquire()` — İcazə almağa cəhd edir, alınsa true, yoxdursa false.

### ⚙️ Thread Pool-lar (`ExecutorService`)
- `execute(Runnable task)` — Runnable tipli task icra edir.
- `submit(Callable/Void task)` — Task göndərir və gələcək nəticə (Future) qaytarır.
- `shutdown()` — Pool-u bağlayır, yeni iş qəbul etmir.
- `shutdownNow()` — Pool-u dərhal bağlayır, işləyən thread-ləri dayandırır.
- `awaitTermination(timeout, unit)` — Pool-un tam bağlanmasını gözləyir.

### 🛡️ tryLock()
- `ReentrantLock` metodudur.
- Lock almağa cəhd edir, əgər alınsa true, yoxdursa false qaytarır.
- `Deadlock`-ları önləmək və ya alternativ mexanizm işlətmək üçün istifadə olunur.

### 🕵️ Deadlock detection (`ThreadMXBean`)
- `findDeadlockedThreads()` — Hal-hazırda deadlock-da olan thread-lərin ID-lərini qaytarır.
- `findMonitorDeadlockedThreads()` — synchronized bloklarında kilidlənən thread-ləri qaytarır.

### 📢 wait() / notify() / notifyAll()
- `wait()` — Thread-i wait vəziyyətinə salır və `notify()` və ya `notifyAll()` gələnədək gözləyir.
- `notify()` — wait-də gözləyən thread-lərdən birini oyadır.
- `notifyAll()` — wait-də gözləyən bütün thread-ləri oyadır.
Yalnız `synchronized` blok içində işləyir.

### 📌 Condition (ReentrantLock ilə)
- `await()` — Thread-i wait() kimi gözləməyə salır.
- `signal()` — `await()`-də gözləyən thread-lərdən birini oyadır.
- `signalAll()` — `await()`-də gözləyən bütün thread-ləri oyadır.
- `ReentrantLock`-un daha çevik və inkişaf etmiş sinxronizasiya mexanizmidir.

## 2️⃣1️⃣ ExecutorService nədir?

- **`ExecutorService`** — Java-da thread pool-ları idarə edən interfeysdir.
- Yeni thread yaratmaq əvəzinə, hazır thread-lərdən istifadə edərək işləri icra edir.
- Yəni thread-ləri sistemli və nəzarətli şəkildə idarə etməyə imkan verir.

### 📌 Əsas Metodları və Nə İş Görür?

| Metod                             | Nə edir?                                               |
| :-------------------------------- | :----------------------------------------------------- |
| `execute(Runnable command)`       | Runnable tipli iş icra edir, nəticə qaytarmır.         |
| `submit(Runnable task)`           | Runnable task icra edir, `Future` qaytarır.            |
| `submit(Callable task)`           | Callable task icra edir, `Future` ilə nəticə qaytarır. |
| `shutdown()`                      | Yeni iş qəbul etməyi dayandırır.                       |
| `shutdownNow()`                   | Bütün işləyən thread-ləri dayandırmağa cəhd edir.      |
| `awaitTermination(timeout, unit)` | Pool-un bağlanmasını müəyyən müddət gözləyir.          |
| `isShutdown()`                    | Pool-un bağlanıb-bağlanmadığını yoxlayır.              |
| `isTerminated()`                  | Bütün işlər bitib-bitmədiyini yoxlayır.                |

**📌 Kod Nümunəsi:**

```java
import java.util.concurrent.*;

public class ExecutorServiceExample {
    public static void main(String[] args) {
        // 5 thread-lik thread pool yaradırıq
        ExecutorService executor = Executors.newFixedThreadPool(5);

        // Runnable task (geri dəyər qaytarmır)
        Runnable task1 = () -> System.out.println("Runnable iş icra olunur");

        // Callable task (geri dəyər qaytarır)
        Callable<String> task2 = () -> {
            Thread.sleep(1000);
            return "Callable nəticəsi";
        };

        // execute() - Runnable iş göndərir, Future qaytarmır
        executor.execute(task1);

        // submit() - Runnable iş göndərir, Future qaytarır
        Future<?> future1 = executor.submit(task1);

        // submit() - Callable iş göndərir, Future qaytarır
        Future<String> future2 = executor.submit(task2);

        try {
            // Callable işin nəticəsini alırıq
            String result = future2.get();
            System.out.println(result);
        } catch (InterruptedException | ExecutionException e) {
            e.printStackTrace();
        }

        // Pool-u bağlayırıq
        executor.shutdown();
    }
}
```

## 2️⃣2️⃣ ExecutorServiceScheduler nədir?

- **`ScheduledExecutorService`** — ExecutorService-in ixtisaslaşmış versiyasıdır.
- Müəyyən bir gecikmə ilə və ya dövrü (periodic) iş icra etmək üçün istifadə olunur.

### 📌 Əsas Metodları:

| Metod                                                                                    | Nə edir?                                                             |
| :--------------------------------------------------------------------------------------- | :------------------------------------------------------------------- |
| `schedule(Runnable command, long delay, TimeUnit unit)`                                  | Verilən gecikmə ilə Runnable iş icra edir.                           |
| `schedule(Callable command, long delay, TimeUnit unit)`                                  | Verilən gecikmə ilə Callable iş icra edir.                           |
| `scheduleAtFixedRate(Runnable command, long initialDelay, long period, TimeUnit unit)`   | Verilən interval ilə işləri **sabit aralıqla** icra edir.            |
| `scheduleWithFixedDelay(Runnable command, long initialDelay, long delay, TimeUnit unit)` | Hər iş bitəndən sonra **müəyyən gecikmə ilə** növbəti işi icra edir. |

**📌 Kod Nümunəsi:**

```java
import java.util.concurrent.*;

public class ScheduledExecutorExample {
    public static void main(String[] args) {
        // 2 thread-lik scheduler
        ScheduledExecutorService scheduler = Executors.newScheduledThreadPool(2);

        Runnable task = () -> System.out.println("Gecikmiş və ya dövrü iş");

        // 3 saniyə gecikmə ilə işə sal
        scheduler.schedule(task, 3, TimeUnit.SECONDS);

        // Hər 5 saniyədən bir işlə
        scheduler.scheduleAtFixedRate(task, 1, 5, TimeUnit.SECONDS);

        // Hər iş bitəndən 5 saniyə sonra növbəti
        scheduler.scheduleWithFixedDelay(task, 1, 5, TimeUnit.SECONDS);
    }
}
```

## 2️⃣3️⃣ execute() vs submit() fərqi nədir?

| Xüsusiyyət        | `execute()`                                                    | `submit()`                                   |
| :---------------- | :------------------------------------------------------------- | :------------------------------------------- |
| İcra etdiyi iş    | Yalnız **Runnable** qəbul edir.                                | **Runnable və Callable** qəbul edir.         |
| Nəticə qaytarır?  | Xeyr                                                           | Bəli — **Future** obyekt qaytarır.           |
| Exception idarəsi | Exception atılsa, **Executor-un default handler-i** çağırılır. | Exception **Future.get()** çağıranda atılır. |

## 2️⃣4️⃣ Runnable, Callable, Future nədir?

### 🔸 Runnable
- `run()` metodu var.
- Heç bir nəticə qaytarmır və exception atmaz.

```java
Runnable task = () -> System.out.println("iş gedir");
```

### 🔸 Callable
- `call()` metodu var.
- Nəticə qaytarır və exception ata bilər.

```java
Callable<String> task = () -> "nəticə";
```

### 🔸 Future
- `submit()` metodunun geri qaytardığı obyekt.
- Task-in nəticəsini sonradan almağa imkan verir.
- **Əsas metodları: **
  - `get()` → Nəticəni qaytarır, yoxsa gözləyir.
  - `isDone()` → İş bitibmi?
  - `cancel()` → Task-i dayandır.
  - `isCancelled()` → Task dayandırılıb?

```java
Future<String> result = executor.submit(callable);
String value = result.get();
```

### 📌 Runnable mi, Callable mi seçəcəyik? Nə vaxt hansını?

#### 🔴 Runnable → Əgər:
Task nəticə qaytarmalı deyilsə

- Sadəcə iş icra olunmalıdırsa (məs: faylı silmək, məlumat çap etmək, faylı yükləmək və s.)
- Exception-ları manual sinxron şəkildə idarə etmək lazım deyilsə
- `execute()` və ya `submit()` metodları ilə işləmək istədikdə (`Future` lazım deyilsə)

**Misal:**
- Log faylına mesaj yazmaq üçün thread lazımdır → Runnable

#### 🔵 Callable → Əgər:
- Task nəticə qaytarmalıdırsa
- Task icrası zamanı `Exception` ata bilərsə
- Task-in işinin bitməsini gözləyib nəticəni `Future.get()` ilə almaq istəyiriksə
- Daha kompleks asinxron hesablama və ya məlumat dönmək lazımdırsa

**Misal:**
- Bir serverdən məlumat alıb gələn `JSON`-u qaytarmaq → `Callable`

#### 📌 Seçim meyarı:

| Sual                               | Cavab | Seçim    |
| :--------------------------------- | :---- | :------- |
| Task nəticə qaytaracaq?            | Bəli  | Callable |
| Exception ata bilər?               | Bəli  | Callable |
| Task sadəcə iş görəcək?            | Bəli  | Runnable |
| Nəticə lazım deyil?                | Bəli  | Runnable |
| Nəticəni sonradan almaq istəyirəm? | Bəli  | Callable |


#### 📌 Real Misallar:

**✅ Runnable:**

```java
Runnable cleanLogs = () -> System.out.println("Loglar silindi");
executor.execute(cleanLogs);
```

**✅ Callable:**

```java
Callable<String> fetchData = () -> {
    Thread.sleep(1000);
    return "Serverdən data";
};
Future<String> data = executor.submit(fetchData);
String result = data.get();
System.out.println(result);
```

## 👉 Future — bir thread-in (və ya task-in) nə vaxt bitəcəyini izləmək, istəsən dayandırmaq və ən əsası iş bitəndə onun nəticəsini almaq üçün istifadə olunur.


### 📌 Runnable vs Callable fərqi

| Xüsusiyyət             | Runnable | Callable |
| :--------------------- | :------- | :------- |
| Metod adı              | `run()`  | `call()` |
| Nəticə qaytarır?       | Xeyr     | Bəli     |
| Exception atır?        | Xeyr     | Bəli     |
| submit() ilə işləyir?  | Bəli     | Bəli     |
| execute() ilə işləyir? | Bəli     | Xeyr     |

### 📌 Yekun Cədvəl

| İstifadə     | Metod                      | Task tipi         | Nəticə     |
| :----------- | :------------------------- | :---------------- | :--------- |
| İş icra et   | `execute(Runnable)`        | Runnable          | Yox        |
| İş icra et   | `submit(Runnable)`         | Runnable          | Future\<?> |
| İş icra et   | `submit(Callable)`         | Callable          | Future<T>  |
| Gecikməli iş | `schedule()`               | Runnable/Callable | Future     |
| Dövrü iş     | `scheduleAtFixedRate()`    | Runnable          | —          |
| Dövrü iş     | `scheduleWithFixedDelay()` | Runnable          | —          |




