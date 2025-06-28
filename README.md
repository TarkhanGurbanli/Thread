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




