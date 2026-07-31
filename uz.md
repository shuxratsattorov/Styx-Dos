# Styx Token Manager —  Qo'llanma

## 1. Dastur nima qiladi

**Styx Token Manager (StyxClient)** — elektron raqamli imzo (ЭЦП) klienti. U kompyuteringizda
fonda ishlab turadi va bank tizimlariga (internet-bank, iABS va shu kabi dasturlar) tokeningizdagi
kalit bilan hujjat imzolash imkonini beradi.

---

## 2. Tizim talablari

| Talab | Qiymat |
|---|---|
| Operatsion tizim | Windows 10 / 11 (64-bit) |
| Huquq | O'rnatish uchun **administrator** huquqi |

---

## 3. O'rnatish

1. Sizga berilgan **`StyxClient.msi`** faylini oling.
2. Fayl ustiga o'ng tugma bosing → **«Запуск от имени администратора»** (administrator nomidan
   ishga tushirish).
3. O'rnatish jarayonida token drayveri (ePass) va CNG komponentlari ham o'rnatiladi. Bu bir necha daqiqa
   vaqt olishi mumkin — oynani yopmang.
4. O'rnatish tugagach kompyuterni **qayta yuklang** (drayver to'liq ishga tushishi uchun).

**Avtomatik ishga tushish:** dastur Windowsga kirganingizda o'zi ishga tushadi — uni har safar
qo'lda ochish shart emas.

---

## 4. Dastur qayerda? — trey belgisi

Dasturning alohida katta oynasi yo'q. U ekranning o'ng pastki burchagidagi trey sohasida — soat yonida yoki ∧ tugmasi ostidagi yashirin belgilar orasida — kichik belgi (ikonka) ko'rinishida turadi.

Belgi rangi tokeningiz holatini bildiradi:

| Rang | Ma'nosi | Nima qilish kerak |
|---|---|---|
| ⚫ **Qora** | Dastur hali faol emas: token ulanmagan yoki PIN tasdiqlanmagan | Tokenni USB-portga ulang va **«Вход»** oynasida PINni kiriting |
| 🟡 **Sariq** | Token ulangan, lekin unda sertifikat yo'q | Bankka murojaat qiling — tokenga sertifikat yozilishi kerak |
| 🟢 **Yashil** | Dastur faol, imzolashga tayyor | Ishlashingiz mumkin |

**Belgi ustiga o'ng tugma bossangiz** — asosiy menyu ochiladi.

---

## 5. Kundalik ish tartibi

### 5.1. Tokenni ulash va PIN kiritish

1. Tokenni USB-portga ulang.
2. Bir necha soniyadan so'ng **«Вход»** (Kirish) oynasi ochiladi.
3. **PIN-kodingizni** kiriting va **«Войти»** tugmasini bosing.
4. PIN to'g'ri bo'lsa, trey belgisi **yashil** holatga o'tadi.

> **Diqqat:** oyna **2 daqiqadan so'ng o'zi yopiladi**. Yopilib qolsa, tokenni chiqarib qayta ulang.

> **Diqqat:** PINni ketma-ket **3 marta xato** kiritsangiz, token **bloklanadi**. Bloklangan
> tokenni faqat bank/xizmat markazi ochib bera oladi.

### 5.2. Sessiya muddati

Muvaffaqiyatli kirgandan so'ng sessiya **10 daqiqa** amal qiladi. Shu vaqt o'tgach **«Вход»**
oynasi qayta ochilib, PINni yana so'raydi.

Sessiya holatini **«Настройки»** oynasidan ko'rish mumkin.

---

## 6. PIN-kodni o'zgartirish

1. Trey belgisiga o'ng tugma bosing → token bandini oching → **«Сменить PIN»**.
2. Ochilgan oynada:
   - **«Введите старый PIN»** — hozirgi PIN;
   - **«Введите новый PIN»** — yangi PIN;
   - **«Повторите новый PIN»** — yangi PINni takrorlang.
3. **OK** tugmasini bosing.

**Yangi PINga qo'yiladigan talablar** (oynada ham ko'rsatiladi):

- kamida **6 ta belgi**;
- kamida **1 ta bosh harf** (A–Z);
- kamida **1 ta maxsus belgi**: `*`, `-`, `=`, `+`;
- yangi PIN eskisidan farq qilishi shart.

To'g'ri PINga misol: `Bank-2026`

---

## 7. Sozlamalar oynasi («Настройки»)

Bu oyna asosan **holatni tekshirish** uchun kerak. Undagi ma'lumotlar:

| Bo'lim | Nima ko'rsatadi |
|---|---|
| HTTP / WebSocket serverlar | Yashil nuqta — ishlayapti, qizil — to'xtagan |
| **Авторизован / Не авторизован** | Sessiya holati |
| Qolgan vaqt | Sessiya tugashiga qancha qolgani (soat:daqiqa:soniya) |
| Token turi va seriya raqami | Ulangan token haqida ma'lumot |

Tugmalar: **«Запустить» / «Остановить»** — serverni ishga tushirish/to'xtatish,
**«Сохранить»** — port raqamlarini saqlash.

> **Port raqamlarini (6210, 6211, 8181) o'zgartirmang** — bank tizimlari aynan shu portlarga
> murojaat qiladi. Ularni faqat texnik xodim ko'rsatmasi bilan o'zgartiring.

---

## 8. Dasturdan chiqish va qayta ishga tushirish

Trey menyusi → **«Выход»**. Tasdiqlash so'raladi:

> «Внимание! Завершение программы влечет за собой остановку функций ЭЦП и шифрования…»

**«Да»** ni bossangiz, dastur to'liq yopiladi. Qayta ishga
tushirish: «Пуск» → **StyxClient** → **Styx Token Manager**.

---

## 9. Tez-tez uchraydigan muammolar

| Muammo / xabar | Sababi | Yechimi |
|---|---|---|
| Treyda dastur belgisi yo'q | Dastur ishga tushmagan | «Пуск» → StyxClient → Styx Token Manager. Belgi treydagi **∧** tugmasi ostida yashirinmaganini ham tekshiring |
| **«Программа уже запущена»** | Dastur allaqachon ishlab turibdi | Ikkinchi nusxa kerak emas — treydagi belgidan foydalaning |
| Token ulangan, lekin ko'rinmayapti | USB-port, drayver yoki token bilan muammo | Boshqa USB-portga ulang; kompyuterni qayta yuklang; muammo qolsa — bankka murojaat qiling |
| Bank sayti/dasturi «klient topilmadi» deydi | Dastur ishlamayapti yoki server to'xtagan | Dasturni ishga tushiring; **«Настройки»** oynasida HTTP va WebSocket yashil ekanini tekshiring, kerak bo'lsa **«Запустить»** ni bosing |
| **«Введен неверный PIN»** | Xato PIN kiritilgan | PINni diqqat bilan qayta kiriting. **3 marta xato = token bloklanadi** |
| Token bloklandi / PIN unutildi | Urinishlar soni tugagan | Faqat bank/xizmat markazi ochib beradi — murojaat qiling |
| Imzolashda PIN qayta-qayta so'ralmoqda | Sessiya 10 daqiqada tugaydi; ba'zi banklarda har imzoga PIN so'raladi | Normal holat — PINni kiriting |
| Kirish oynasi o'zi yopilib qoldi | Oyna 2 daqiqadan so'ng avtomatik yopiladi | Tokenni qayta ulang yoki amalni qaytadan boshlang |
