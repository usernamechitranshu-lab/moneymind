# 📘 MoneyMind: Complete Step-by-Step Setup Guide
### (Bilkul Aasan Bhasha Me — Non-Technical Users Ke Liye)
**Created with ❤️ by Chitranshu Shrivastava**

> 💡 **Yeh guide kiske liye hai?**  
> Agar aapne zindagi me kabhi coding nahi ki hai, tab bhi aap agle **10 se 15 minute** me apna poora MoneyMind app live kar lenge. Har ek step ka direct link aur button ka rang tak niche bataya gaya hai.

---

## 📑 Setup ke 5 Simple Steps

```
[Step 1] Google Account & Free AI Key nikalna (3 Minute)
   ⬇️
[Step 2] Google Sheet & Apps Script Setup (1-Click Auto-Create) (4 Minute)
   ⬇️
[Step 3] Web App Live Karna (GitHub Pages ya Local Browser) (3 Minute)
   ⬇️
[Step 4] Phone Me App Install Karna (Android & iPhone) (1 Minute)
   ⬇️
[Step 5] Family Members Ke Gmail Connect Karna (Optional / 3 Minute)
```

---

## 🟢 STEP 1: Gemini AI Key Nikalna (Bilkul Free)

Gemini AI aapki aawaz, likhe hue hisaab ki photos aur bank SMS ko samajhkar automatically categorize karta hai. Iska official free account aise banayein:

1. Apne browser (Chrome/Safari) me yeh link kholein:  
   👉 **[aistudio.google.com/apikey](https://aistudio.google.com/apikey)**
2. Apne normal Google (Gmail) account se Sign In karein.
3. Blue (Neela) color ka button dikhega: **"Create API key"** ➔ Is par click karein.
4. Popup aayega: **"Create API key in new project"** chunein.
5. Ek lambi key aayegi (jaise `AIzaSyD...`). Uske paas bane **Copy** icon par click karein.
6. Apne Notepad me ise save kar lein:  
   `KEY_1 = AIzaSyD...`
7. *(Optional par badiya)*: Agar aap chahte hain ki heavy use me bhi app kabhi na ruke, toh wahi button **"Create API key"** do baar aur daba kar 2 aur keys nikaal lein (`KEY_2`, `KEY_3`).

---

## 🟢 STEP 2: Google Apps Script & Sheet Setup (Automatic)

Aapko Google Sheet me koi table ya column nahi banana — hamara code khud aapke Google Drive me sheet bana dega!

### 1. Script Editor Kholna
1. Browser me yeh link open karein:  
   👉 **[script.google.com/home/start](https://script.google.com/home/start)**
2. Top left me **"+ New project"** button par click karein.
3. Top left me jahan *"Untitled project"* likha hai, us par click karke naam badal kar **`MoneyMind Backend`** likh dein aur **Rename** karein.

### 2. Code Paste Karna
1. Screen ke beech me jo pehle se likha hua code dikh raha hai (`function myFunction() ...`), use poora select karke (`Ctrl + A` ya `Cmd + A`) **Delete** kar dein.
2. Hamare project ki file [`Code.gs`](file:///g:/Google%20antigravity/my%20project/Code.gs) ka saara code copy karein aur wahan paste kar dein.
3. Top toolbar me **Save icon 💾 (Floppy Disk)** par click karein.

### 3. API Key Save Karna
1. Left sidebar me sabse neeche bane **Gear Icon ⚙️ (Project Settings)** par click karein.
2. Page ke neeche scroll karein jahan **"Script Properties"** likha hai.
3. **"Add script property"** par click karein:
   - **Property**: `GEMINI_API_KEYS`
   - **Value**: Apni Step 1 wali keys daalein (agar ek hai toh `KEY_1`, agar 3 hain toh comma laga kar: `KEY_1,KEY_2,KEY_3`).
4. Blue button **"Save script properties"** par click karein.

### 4. Ek Click Me Sheet Auto-Create Karna
1. Left sidebar me wapas **Code Editor (<>)** icon par click karein.
2. Top bar me jahan dropdown hai (jisme functions ke naam hote hain), wahan se chunein:  
   👉 **`setupInitialSheets`**
3. Barabar me bane **Run (▶️ Play Button)** par click karein.
4. **Google Permission Popup Aayega (Yeh normal hai):**
   - Click: **"Review permissions"**
   - Apna Google Account select karein.
   - Ek warning aayegi: *"Google hasn't verified this app"* ➔ Ghabrayein nahi, yeh aapka apna private code hai. Click karein **"Advanced"** (chhota sa neeche likha hoga).
   - Click karein **"Go to MoneyMind Backend (unsafe)"**.
   - Neeche scroll karke click karein **"Allow"**.
5. Neeche *Execution log* me likha aayega:  
   `🎉 Nayi Google Sheet automatically ban gayi hai! URL: https://docs.google.com/spreadsheets/d/...`  
   *(Aapke Google Drive me saari 8 sheets apne aap ban gayi hain!)*

### 5. Automatic Triggers Lagana
1. Wahi top dropdown se chunein:  
   👉 **`setupAllTriggers`**
2. Click karein **Run (▶️)**.  
   *(Isse automated queue, monthly expense report, aur Gmail auto-sync start ho jayenge).*

### 6. Web App Deploy Karna (Link Nikalna)
1. Top right corner me blue color ka **"Deploy"** button dabayein ➔ Chunein **"New deployment"**.
2. Left side me **Gear icon ⚙️** par click karke chunein **"Web app"**.
3. Form me bas yeh bharein:
   - **Description**: `MoneyMind v3.5`
   - **Execute as**: **"Me (aapka_email@gmail.com)"**
   - **Who has access**: **"Anyone"** *(Yeh sabse zaroori hai! Taki aapke phone se entry ho sake).*
4. Click karein **"Deploy"**.
5. Screen par ek **Web app URL** aayegi (jo `/exec` par khatam hoti hai).  
   👉 **Is URL ko Copy karke Notepad me rakh lein!** Yeh aapke app ka main connection link hai.

---

## 🟢 STEP 3: Frontend Web App Live Karna

Aapke paas 2 aasan vikalp hain:

### Vikalp A: GitHub Pages Par Free Host Karna (Recommended)
Agar aap chahte hain ki aap kisi bhi phone ya computer se bina file khole use kar sakein:
1. Browser me open karein: 👉 **[github.com/new](https://github.com/new)**
2. Repository name me likhein: **`moneymind`**.
3. **Public** chunein aur click karein **"Create repository"**.
4. Screen par **"uploading an existing file"** link par click karein.
5. Hamare folder se **`index.html`** aur **`webapp.html`** dono files drag-and-drop karke upload kar dein aur green button **"Commit changes"** daba dein.
6. Upar menu me **Settings ⚙️** par jayein ➔ Left sidebar me **Pages** par click karein.
7. **Branch** dropdown me `None` ki jagah **`main`** select karein aur **Save** karein.
8. 1 minute baad page refresh karein, aapko upar aapka live link mil jayega:  
   `https://aapka-username.github.io/moneymind/`

### Vikalp B: Bina GitHub Ke Local Chalana (Sabse Fast)
Agar aap turant test karna chahte hain:
- Apne computer ke folder me jakar **`index.html`** par double click karein. Yeh Chrome ya Edge me seedhe open ho jayega!

---

## 🟢 STEP 4: Web App Ko Google Sheet Se Connect Karna

1. Apne phone ya computer me MoneyMind web app kholein.
2. Top right corner me bane **Gear Icon ⚙️ (Settings)** par click karein.
3. Popup me 2 cheezein paste karein:
   - **Google Apps Script Web App URL**: Step 2.6 me copy ki hui URL (ends with `/exec`).
   - **Gemini API Key**: Step 1 wali `KEY_1`.
4. Click karein **"Save Settings"**.
5. Top bar me green dot 🟢 dikhega — iska matlab aapka app Google Sheets se successfully connect ho chuka hai!

### 📱 Phone Me App Icon Kaise Lagayein?
- **Android**: Chrome me link kholein ➔ Upar 3 dots `⋮` dabayein ➔ **"Add to Home screen"** ya **"Install App"** dabayein.
- **iPhone**: Safari me link kholein ➔ Neeche Share icon (Arrow box) dabayein ➔ **"Add to Home Screen"** dabayein.  
*(Aapke phone ke home screen par Luxury 'MM' icon ka app ban jayega jo native app ki tarah khulta hai).*

---

## 🟢 STEP 5: Multiple Family Gmails & PAN Cards Setup (Control Hub)

Top right me bane **🎛️ Control Hub** icon par click karein. Yahan 6 simple tabs hain:

### 1. 🆔 PAN Cards & Family Demats Tab:
- Agar aap ghar ke alag-alag members ke naam se IPO lagate hain:
  - Holder Name (e.g. `Mummy`)
  - PAN Card (e.g. `ABCDE1234F`) — Privacy ke liye yeh `ABCDE••••F` dikhega.
  - Broker (e.g. `Zerodha`, `Groww`, `AngelOne`)
  - Bank (e.g. `SBI`, `IOB`)
- Click **"Save PAN Profile"**. Ab IPO lagate waqt aap sirf member select karenge.

### 2. 📧 Connected Gmails Tab (Family Auto-Tracking):
Family members ke phone me koi software install nahi karna. Bas unke Gmail se IPO emails aapke paas auto-forward hongi:
1. Hub me **"Connected Gmails"** tab me jakar **"Copy Query"** button dabayein.
2. Family member ke laptop me unka Gmail kholein:  
   👉 Direct Settings Link: **[mail.google.com/mail/u/0/#settings/filters](https://mail.google.com/mail/u/0/#settings/filters)**
3. **"Create a new filter"** par click karein.
4. **"Has the words"** box me copied text paste karein:  
   `mandate OR "blocking of funds" OR "UPI 2.0 LIEN" OR "unblocked" OR "allotment"`
5. Click **"Create filter"**.
6. Check karein **"Forward it to:"** ➔ Apni primary Gmail ID chunein aur Save karein.
7. Hub me unka email add kar dein.
8. Test karne ke liye Hub me **"Scan Inboxes Now 🔄"** button dabayein — saari emails scan ho kar sheet me entry ban jayegi!

---

## 🎯 Quick Verification: Sab Kuch Kaam Kar Raha Hai?

1. **Voice / Text Entry**: Chat me likhein:  
   `Chai nashta 40 rupaye cash` ➔ Enter dabayein ➔ Turant entry Expenses tab me add ho jayegi.
2. **Camera OCR**: Camera 📷 icon dabakar kisi bhi likhe hisaab ya receipt ki photo kheenchein ➔ AI use padhkar expense create kar dega.
3. **IPO Screenshot**: PhonePe/GPay ke mandate ka screenshot 📎 attach karein ➔ AI auto-detect karke IPO tab me mandate lock kar dega.
4. **IPO Stuck Alert**: Agar kisi IPO ka paisa 7 din se fasa hai, toh IPO Tracker tab me laal warning banner dikhai dega.

Aapka MoneyMind 100% ready hai! 🎉
