**1. HTTP (Hypertext Transfer Protocol)** <br>
Alohaga asoslangan: HTTP protokoli har bir so'rov uchun yangi aloqalarni o'rnatadi. So'rov yuborilganidan keyin aloqalar yopiladi.
Stateless (Holatni saqlamaydi): HTTP server va mijoz o'rtasida aloqaning holatini saqlamaydi. Har bir so'rov mustaqil va alohida ishlanadi.
Ishlash usuli: Har bir HTTP so'rovi mustaqil bo'lib, serverdan qaytgan javobdan so'ng aloqalar yopiladi. Agar real vaqtda xabarlar yuborish kerak bo'lsa, uzoq polling (long polling) yoki server-sent events (SSE) kabi usullar talab qilinadi.
Foydalanish sohalari: Veb-sahifalar, resurslarni yuklash, API so'rovlari.
<br>**2. WebSocket** <br>
Doimiy aloqalar (Full-duplex): WebSocket doimiy aloqalarni o'rnatadi. Server va mijoz o'rtasida bir marta aloqani o'rnatganidan so'ng, ular o'rtasida ikki tomonlama (full-duplex) aloqada bo'lishi mumkin.
Real-vaqt aloqalari: WebSocket protokoli mijoz va server o'rtasida aniq vaqtda xabarlarni yuborishni ta'minlaydi. Bu xususiyatni chat ilovalari, o'yinlar, real-vaqt monitoring tizimlari va boshqalarda ishlatish mumkin.
Ishlash usuli: HTTP so'rovi orqali WebSocket ulanishi o'rnatiladi (HTTP handshaking). So'ng, WebSocket aloqasi orqali real-vaqtda xabarlar almashiladi.
Foydalanish sohalari: Chat tizimlari, onlayn o'yinlar, real-vaqt xabarlar (stocks, sports, notification), video oqim (streaming).
 #### WebSocket va HTTP protokollari:
```
                                   +--------------------------------+
                                   |      HTTP Protokoli            |
                                   +--------------------------------+
                                   |                                |
                                   |  1. Mijozdan so'rov yuboriladi |
                                   |  2. Server javob beradi        |
                                   |  3. Aloqa yopiladi             |
                                   |  4. Har bir so'rov alohida     |
                                   |     ishlanadi (stateless)      |
                                   |                                |
                                   +--------------------------------+
                                             ↓
                                (Har bir so'rov alohida, aloqalar yopiladi)
                                             ↓
                                    +--------------------------------+
                                    |     WebSocket Protokoli        |
                                    +--------------------------------+
                                    |                                |
                                    |  1. HTTP so'rovi orqali        |
                                    |     ulanish boshlanadi         |
                                    |  2. Server WebSocketni         |
                                    |     qo'llab-quvvatlasa,        |
                                    |     aloqalar doimiy bo'ladi    |
                                    |  3. Real vaqtda xabarlar       |
                                    |     yuboriladi                 |
                                    |  4. Full-duplex aloqalar       |
                                    |  5. Mijoz va server bir-biriga |
                                    |     xabar yuborishadi          |
                                    |                                |
                                    +--------------------------------+
```
```
 Client (User 1)                              Client (User 2)
      |                                               |
      | HTTP Request --->  [WebSocket Handshake] ---> |
      |                                               |
      |<--- HTTP Response <--- [WebSocket Handshake]--|
      |                                               |
      |                                               |
  WebSocket: Doimiy aloqalar (Full-Duplex)            |
      |<--- Xabarlar Yuboriladi (Real-Time) --->|     |
      |                                               |
      |<--- Xabarlar Yuboriladi (Real-Time) --->|     |
      |                                               |
  WebSocket: So'rovni yopish                          |
```
