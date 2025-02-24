# M322-M165 Projektarbeit

## Frontend-Planung mit Figma für den Film- & Serien-Tracker (Angular + CouchDB)

Figma ist perfekt, um das UI-Design deines Angular-Frontends visuell zu planen. Hier ist eine Schritt-für-Schritt-Anleitung, wie du das machst:

### 1️⃣ Projektstruktur in Figma anlegen
- Erstelle eine neue Datei in Figma
- Definiere deine Frames (Seiten)
  - **Desktop-Version**: 1440x1024 px
  - **Mobile-Version**: 375x812 px (iPhone 13)
- Setze ein Grid oder Layout-Raster (8px oder 12px Grid für ein sauberes Design)

### 2️⃣ Wichtige Screens entwerfen
Hier sind die Hauptseiten, die du in Figma designen solltest:

#### 📌 1. Startseite (Home)
- **Header**: Logo, Navigation, Suchleiste
- **Hauptbereich**:
  - Empfohlene Filme & Serien (große Thumbnails)
  - Trending Filme & Serien (Karussell oder Grid)
  - Top-Bewertungen deiner Freunde
- **Footer**: Links, AGB, Impressum

#### 📌 2. Detailseite eines Films/Serie
- Filmcover + Titel
- Beschreibung, Genre, Jahr, Laufzeit
- Bewertungen & Rezensionen (von anderen Nutzern)
- "Zur Watchlist hinzufügen"-Button

#### 📌 3. Watchlist-Seite
- Liste aller gespeicherten Filme & Serien
- Möglichkeit, sie als "Gesehen" zu markieren
- Sortier- und Filterfunktionen (z. B. nach Genre, Jahr)

#### 📌 4. Profilseite
- Nutzerbild, Username, Statistiken (gesehene Filme, Lieblingsgenres)
- Freundesliste & deren Filmaktivitäten
- Einstellungen (Passwort ändern, Account verwalten)

#### 📌 5. Login & Registrierung
- Einfache Formulare für Anmeldung & Registrierung
- Optionale Social Media Logins (Google, Facebook)

### 3️⃣ UI-Design in Figma umsetzen

#### 🎨 Farbpalette & UI-Stil definieren

| Farbe       | Hex-Code  | Verwendung                  |
|------------|----------|----------------------------|
| Dunkelgrau | #121212  | Hintergrund                 |
| Rot        | #E50914  | Buttons, Highlights         |
| Weiß       | #FFFFFF  | Text                         |
| Grau       | #B3B3B3  | Untertitel, Icons           |

#### 📦 UI-Komponenten erstellen
- 🔍 **Suchleiste** mit Angular Material `mat-form-field`
- 📊 **Bewertungs-Sterne** mit Angular Material `mat-icon`
- 🛑 **"Zur Watchlist hinzufügen"-Button** als Floating Action Button
- 📏 **Responsive Layouts** mit Auto Layout in Figma testen

### 4️⃣ Prototyping & Testing in Figma
- ✅ Interaktive Klickflächen setzen (z. B. "Watchlist" → Profilseite)
- ✅ Navigation testen (z. B. Menü öffnet sich)
- ✅ Mobile-First testen (Responsive Breakpoints in Figma setzen)

### 📥 Export & Implementierung in Angular
Sobald das Design fertig ist, kannst du es in dein Angular-Projekt überführen:
- 🔹 SVGs oder PNGs exportieren für Icons & Logos
- 🔹 CSS-Styles aus Figma kopieren (`Figma → Inspektor → CSS-Code`)
- 🔹 Komponenten strukturieren basierend auf den Figma-Frames

## 🚀 Nächste Schritte
1. Figma-Design starten → Screens & UI-Elemente erstellen
2. Interaktive Prototypen bauen → Testen & Feedback einholen
3. In Angular umsetzen → Komponenten aus Figma nachbauen

---

## 📽️ Film- und Serien-Tracker mit Angular & CouchDB

### 🛠️ Tech-Stack
- **Frontend**: Angular mit Angular Material für UI-Komponenten
- **Backend**: CouchDB (NoSQL-Datenbank mit Dokumenten für Filme, Nutzer, Bewertungen)
- **API-Server**: Node.js + Express als Middleware für CouchDB
- **Benutzer-Authentifizierung**: CouchDB `_users` oder Firebase Auth
- **Externe API**: TMDb API (für Film- & Serieninfos)
- **Deployment**: Docker für das Backend + Firebase/Netlify für das Frontend

### 📂 Datenstruktur in CouchDB

#### Film-Dokument (movie_12345)
```json
{
  "_id": "movie_12345",
  "type": "movie",
  "title": "Inception",
  "year": 2010,
  "genre": ["Sci-Fi", "Thriller"],
  "ratings": [
    {
      "user_id": "user_5678",
      "rating": 4.5,
      "comment": "Mind-blowing!"
    }
  ],
  "watchlists": ["user_5678", "user_9123"]
}
```

#### Benutzer-Dokument (user_5678)
```json
{
  "_id": "user_5678",
  "type": "user",
  "username": "moviefan123",
  "email": "user@example.com",
  "watchlist": ["movie_12345", "movie_67890"],
  "favorites": ["movie_54321"],
  "friends": ["user_9123"]
}
```

### 🔥 Wichtige Features
- ✅ 📌 **Persönliche Watchlist**: Nutzer können Filme/Serien speichern, als „gesehen“ markieren
- ✅ ⭐ **Bewertungen & Rezensionen**: Filme bewerten, Rezensionen schreiben
- ✅ 👥 **Freundesfunktionen**: Sehen, was Freunde schauen oder empfehlen
- ✅ 📊 **Statistiken & Empfehlungen**: Lieblingsgenre, Anzahl gesehener Filme, empfohlene Filme basierend auf Bewertungen
- ✅ 🔄 **Offline-Synchronisation mit CouchDB**: Dank CouchDB-Replikation auch ohne Internet nutzbar
- ✅ 🎨 **Modernes UI mit Angular Material**: Schnelle, interaktive Benutzeroberfläche

### 🌐 Frontend-Struktur (Angular)

```bash
/src
  /app
    /components
      movie-list.component.ts
      movie-detail.component.ts
      watchlist.component.ts
      review.component.ts
    /services
      movie.service.ts
      user.service.ts
    /pages
      home.component.ts
      profile.component.ts
      login.component.ts
    /models
      movie.model.ts
      user.model.ts
```

### 🚀 Deployment & Hosting
- **Backend mit CouchDB**:
  - CouchDB läuft in einem Docker-Container
  - API wird mit Express.js als Middleware verwaltet
- **Frontend (Angular)**:
  - Deployment mit Firebase Hosting oder Netlify
  - Optional: Angular Universal für serverseitiges Rendering (SSR)
- **Authentifizierung**:
  - CouchDB `_users` oder Firebase Auth für Login/Registrierung

## 📝 Nächste Schritte
1. Angular-Frontend mit Angular Material aufsetzen
2. CouchDB in Docker bereitstellen
3. Express-API für CRUD-Operationen erstellen
4. Watchlist- und Bewertungsfunktionen umsetzen
5. Freundeslisten & Empfehlungen implementieren

