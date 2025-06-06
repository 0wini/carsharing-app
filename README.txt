Carpooling App – Študentské spolujazdy

Komplexná mobilná aplikácia pre študentské spolujazdy, určená výhradne pre používateľov s overeným školským e-mailom. Aplikácia umožňuje ponúkať a rezervovať jazdy medzi univerzitami a mestami, komunikovať cez chat, hodnotiť vodičov a spravovať osobný profil.

---

Funkcionalita

- Registrácia a prihlásenie: výlučne cez overený školský e-mail (napr. @stuba.sk).
- Overenie e-mailu: pomocou e-mailovej služby Mailersend.
- Vyhľadávanie jázd: podľa miesta, dátumu a počtu voľných miest.
- Vytváranie jázd: vodiči môžu zadať trasu, čas, počet miest a cenu.
- Rezervácia jazdy: pasažieri sa môžu prihlásiť na jazdu.
- Chat: komunikácia medzi vodičom a pasažiermi (v štýle Telegramu).
- Profil používateľa: verejný aj súkromný, hodnotenia a recenzie.
- Opakované jazdy: možnosť nastavenia pravidelnosti.
- Notifikácie: pomocou react-native-toast-message.

---

Použité technológie

Frontend (React Native – Expo)
- react-native
- @react-navigation/native
- axios
- react-native-toast-message
- react-native-vector-icons
- react-native-safe-area-context
- @react-native-async-storage/async-storage

Backend (FastAPI)
- fastapi
- uvicorn
- sqlalchemy
- alembic
- python-jose (JWT)
- bcrypt
- Mailersend API
- PostgreSQL databáza

---

Architektúra projektu

Frontend:
carsharing-gui/
├── App.js
├── screens/
│   ├── LoginScreen.js
│   ├── RegisterScreen1.js
│   ├── RegisterScreen2.js
│   ├── SearchRideScreen.js
│   ├── MyRidesScreen.js
│   ├── RideInfoScreen.js
│   ├── ProfileScreen.js
│   └── PublicProfileScreen.js
├── components/
│   ├── BottomMenu.js
│   ├── RideInfo.js
│   └── MyRideInfo.js
└── services/
    └── api.js

Backend:
carsharing-backend/
├── main.py
├── auth.py
├── rides.py
├── models.py
├── schemas.py
├── database.py
└── allowed_domains.json

---

Spustenie aplikácie

Backend:
cd carsharing-backend
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
alembic upgrade head
uvicorn main:app --reload

Frontend:
cd carsharing-gui
npm install
npx expo start

---

API Endpointy

Autentifikácia:
- POST /register – registrácia používateľa
- POST /login – prihlásenie a získanie JWT tokenu
- GET /check-email – kontrola duplicity a domény

Jazdy:
- POST /rides – vytvorenie jazdy
- GET /rides – výpis všetkých jázd
- GET /rides/search – filtrovanie podľa miesta, dátumu, miest
- GET /rides/{ride_id} – detail jazdy
- POST /rides/{ride_id}/join – registrácia na jazdu
- GET /rides/my – jazdy ako pasažier

Používateľ:
- GET /users/me – profil aktuálneho používateľa
- GET /users/{user_id} – verejný profil
- GET /users/{email} – meno a priezvisko používateľa

Hodnotenia:
- POST /reviews – hodnotenie jazdy
- GET /reviews/{user_id} – získanie recenzií

---

Závislosti (vybrané)
- bcrypt – hašovanie hesiel
- jose – tokeny
- Mailersend – odosielanie e-mailov
- alembic – migrácie databázy

---

Budúci vývoj
- Implementácia živého chatu (napr. socket.io alebo napojenie na Telegram API)
- Mapová vizualizácia trasy cez OpenStreetMap
- Push notifikácie pri zmene jazdy
- Administrátorský panel pre moderovanie nahlásených profilov

---

Autor
Vývoj: Dominik Drugda
Študentský projekt v rámci bakalárskej práce na STU FEI
Repozitár obsahuje reálnu aplikáciu vyvinutú a testovanú na emulátore aj reálnych zariadeniach.

---

Licencia
MIT License – viď súbor LICENSE
