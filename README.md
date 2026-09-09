# Transferarbeit Data Science – Credit Card Fraud Detection

Gruppenarbeit (2 Personen) · Modul Data Science · TEKO Luzern
Datensatz **D – Credit Card Fraud Detection** (binäre Klassifikation, stark unbalanciert).

## 1. Repository klonen
```bash
git clone <REPO-URL>
cd DSC_TA_Halter_Nachname2
```

## 2. Umgebung aufsetzen
Beide Geräte identisch – wahlweise conda **oder** venv.

**conda:**
```bash
conda create -n dsc python=3.12 -y
conda activate dsc
pip install -r requirements.txt
```

**venv (Windows):**
```bash
python -m venv .venv
.venv\Scripts\activate
pip install -r requirements.txt
```

## 3. Datensatz beschaffen (NICHT im Repo!)
Die CSV ist ~150 MB und liegt daher in `.gitignore`.
1. Herunterladen von Kaggle: **Credit Card Fraud Detection** (ULB) – `creditcard.csv`
   <https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud>
2. Ablegen unter: `data/creditcard.csv`

Das Notebook lädt relativ: `pd.read_csv("data/creditcard.csv")`.

## 4. nbstripout aktivieren (WICHTIG – vor dem ersten Commit!)
Entfernt Zell-Outputs automatisch vor jedem Commit → schlanke, konfliktarme Merges.
**Jede/r muss das einmal pro Klon ausführen:**
```bash
nbstripout --install
```

## 5. Branch-Workflow
```
main  ── stabile Basis (Teil 1 + Teil 2, Split, evaluate_model)
 ├── feature/model-logreg   (Daniel:  Logistic Regression)
 └── feature/model-rf       (Partner: Random Forest)
```
Kontrakt: beide Modelle nutzen `X_train_scaled, X_test_scaled, y_train, y_test`
und `evaluate_model(...)` aus der Basis. Ergebnis je in `results_logreg` / `results_rf`.

**Ablauf:**
```bash
# Basis steht auf main -> Branch anlegen
git checkout -b feature/model-logreg     # bzw. feature/model-rf

# ... Modell bauen, committen, pushen ...
git push -u origin feature/model-logreg
```
**Merge am Schluss – NACHEINANDER, nicht gleichzeitig:**
1. Erste/r merged seinen Branch nach `main`.
2. Zweite/r holt `main` in seinen Branch (`git merge main`), löst evtl. Mini-Konflikte, merged dann.
3. Auf `main` Teil 4 (Vergleichstabelle + Interpretation) füllen.
4. **`Kernel → Restart & Run All`** – muss fehlerfrei durchlaufen. Das ist der Abgabetest.

## 6. Abgabe
- Datei umbenennen: `DSC_TA_Halter_<Nachname2>.ipynb`
- Notebook (ausführbar) + Kaggle-Link zur CSV per E-Mail an den Dozenten
- Frist: **Fr. 18.09.26, 23:59**
