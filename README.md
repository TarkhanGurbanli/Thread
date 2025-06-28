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
