# 🔥 Firebase Emulator Setup

## What You Get

✅ **ZERO reads billed** - All operations are local  
✅ **Same Firestore API** - No code changes needed  
✅ **Safe testing** - Test new features without affecting production  
✅ **Fast development** - No network latency  
✅ **Emulator UI** - Visual dashboard at http://localhost:4000

---

./install-java.sh

### 2️⃣ Install Firebase CLI (if not already installed)

```bash
npm install -g firebase-tools
```

### 3️⃣ Login to Firebase

```bash
firebase login
```

### 4️⃣ Start the Emulators

**Option A: Emulators Only**
```bash
npm run emulators
```

**Option B: Dev Server + Emulators (recommended)**

Open **two terminal windows**:

**Terminal 1 - Start Emulators:**
```bash
npm run emulators
```

**Terminal 2 - Start Dev Server:**
```bash
npm run dev
```

---

## 📊 Access Points

When emulators are running:

- 🌐 **Your App**: http://localhost:5173 (Vite dev server)
- 🎛️ **Emulator UI**: http://localhost:4000 (View data, users, etc.)
- 📦 **Firestore**: localhost:8080
- 🔐 **Auth**: localhost:9099

---

## 🔄 How It Works

The app **automatically detects** when you're on `localhost` and connects to emulators instead of production Firebase.

Check your browser console - you'll see:
```
🔥 Connected to Firebase Emulators - ZERO reads billed!
```

---

## 💾 Data Persistence

By default, emulator data is **cleared** when you stop the emulators.

### To Export Data (Save State)

```bash
firebase emulators:export ./emulator-data
```

### To Import Data (Restore State)

```bash
firebase emulators:start --import=./emulator-data
```

### Auto-save on Exit

```bash
firebase emulators:start --export-on-exit=./emulator-data
```

---

## 🧪 Testing Workflow

1. **Start emulators**: `npm run emulators`
2. **Start dev server**: `npm run dev` (in separate terminal)
3. **Open app**: http://localhost:5173
4. **Test features** - All reads/writes are FREE!
5. **View data**: http://localhost:4000
6. **Stop emulators**: `npm run stop`
---

## 🔁 Switching Back to Production

Just deploy normally - the emulator connection only activates on `localhost`:

```bash
npm run build
firebase deploy
```

Production builds will use real Firebase automatically.

---

## 🛠️ Troubleshooting

### Port Already in Use?

Change ports in `firebase.json`:
```json
"emulators": {
  "firestore": { "port": 8080 },
  "auth": { "port": 9099 },
  "ui": { "port": 4000 }
}
```

### Emulator Not Connecting?

1. Check emulators are running: http://localhost:4000
2. Check console for "Connected to Firebase Emulators" message
3. Clear browser cache and reload

### Want to Seed Test Data?

Create test users and data through the Emulator UI at http://localhost:4000
 
---

## 📚 Learn More

- [Firebase Emulator Suite Docs](https://firebase.google.com/docs/emulator-suite)
- [Firestore Emulator](https://firebase.google.com/docs/emulator-suite/connect_firestore)
- [Auth Emulator](https://firebase.google.com/docs/emulator-suite/connect_auth)
