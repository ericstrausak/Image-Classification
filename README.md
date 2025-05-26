# 🐍 Reptile & Amphibian Image Classification

## 📘 Project Description
Dieses Projekt klassifiziert verschiedene Arten von Reptilien und Amphibien anhand von Bildern. Als Modell wurde ein **ResNet50** verwendet, das mithilfe von Transfer Learning auf einem benutzerdefinierten Bilddatensatz trainiert wurde.

---

## 🔗 Name & URL

| Name         | URL |
|--------------|-----|
| Huggingface Space | [Zur Anwendung](https://huggingface.co/spaces/Straueri/ReptileAmphibianClassification) |
| Modellseite       | [Zum Modell](https://huggingface.co/Straueri/ReptileAmphibianClassification) |
| GitHub Repository | [Zum Code](https://github.com/ericstrausak/Image-Classification) |

---

## 🏷️ Labels

Die erkannten Arten sind:

```python
['Chameleon', 'Crocodile_Alligator', 'Frog', 'Gecko', 'Iguana', 'Lizard', 'Salamander', 'Snake', 'Turtle_Tortoise']  # <-- aus class_names.json
```

*(Ersetze durch deine tatsächlichen Klassennamen)*

---

## 🗂️ Datenquellen

| Datenquelle         | Beschreibung |
|---------------------|--------------|
| Reptiles Dataset    | Sammlung von Bildern aus öffentlichen Quellen (z. B. Kaggle), sortiert nach Klassenordnern. |
| Manuell annotiert   | Zusätzlich wurden ggf. Bilder aus dem Internet ergänzt und manuell gelabelt. |

---

## 🔄 Datenaufbereitung & Augmentierung

Bilder wurden automatisch aufgeteilt: **70 % Training**, **15 % Validierung**, **15 % Test**.

| Augmentation                  | Beschreibung |
|------------------------------|--------------|
| `Resize(224, 224)`           | Einheitliches Bildformat |
| `RandomHorizontalFlip()`     | Zufällige horizontale Spiegelung |
| `RandomRotation(15)`         | Leichte Bildrotation |
| `ColorJitter(...)`           | Variationen in Helligkeit, Kontrast, Sättigung |

---

## ⚙️ Modellarchitektur

- **Basis:** `torchvision.models.resnet50`
- **Anpassung:** Die finale FC-Schicht wurde an die Anzahl der Klassen angepasst.
- **Optimierer:** Adam
- **Scheduler:** ReduceLROnPlateau
- **Loss Function:** CrossEntropyLoss

---

## 🏋️‍♀️ Trainingsdetails

| Hyperparameter        | Wert |
|-----------------------|------|
| Lernrate              | 0.001 |
| Batch-Größe (Train)   | 32 |
| Batch-Größe (Eval)    | 32 |
| Epochs                | 5–15 |
| Optimizer             | Adam |
| Seed                  | 42 |

---

### 📊 Training Metrics

| Epoch | Training Loss | Validation Loss | Validation Accuracy |
| ----- | ------------- | --------------- | ------------------- |
| 1     | 1.6427        | 1.6613          | 43.39 %             |
| 2     | 1.3473        | 1.3647          | 56.13 %             |
| 3     | 1.1532        | 1.1617          | 62.26 %             |
| 4     | 1.0633        | 1.3981          | 56.37 %             |
| 5     | 0.9705        | 1.3436          | 54.21 %             |
| 6     | 0.8858        | 1.0054          | 66.83 %             |
| 7     | 0.8203        | 1.0476          | 63.94 %             |
| 8     | 0.7609        | 1.0652          | 67.31 %             |
| 9     | 0.7298        | 1.1247          | 63.58 %             |
| 10    | 0.7350        | 1.1176          | 65.87 %             |
| 11    | 0.5006        | 0.7004          | 77.76 %             |
| 12    | 0.4017        | 0.6820          | 78.37 %             |
| 13    | 0.3616        | 0.7138          | 77.52 %             |
| 14    | 0.3333        | 0.7172          | 77.52 %             |
| 15    | 0.3145        | 0.7061          | 78.37 %             |


---

## 🧪 Evaluation

| Klasse                | Precision | Recall | F1-Score | Support |
| --------------------- | --------- | ------ | -------- | ------- |
| Chameleon             | 0.79      | 0.47   | 0.59     | 32      |
| Crocodile\_Alligator  | 0.84      | 0.85   | 0.84     | 104     |
| Frog                  | 0.89      | 0.87   | 0.88     | 75      |
| Gecko                 | 0.52      | 0.59   | 0.55     | 46      |
| Iguana                | 0.75      | 0.68   | 0.71     | 75      |
| Lizard                | 0.63      | 0.61   | 0.62     | 75      |
| Salamander            | 0.81      | 0.74   | 0.77     | 73      |
| Snake                 | 0.73      | 0.81   | 0.77     | 75      |
| Turtle\_Tortoise      | 0.90      | 0.94   | 0.92     | 280     |
| **Gesamt (Accuracy)** |           |        | **0.80** | 835     |
| **Macro Avg**         | 0.76      | 0.73   | 0.74     | 835     |
| **Weighted Avg**      | 0.80      | 0.80   | 0.80     | 835     |



---

## 🔍 Zero-Shot Vergleich (CLIP)

Zusätzlich wurde `openai/clip-vit-b-32` zur Zero-Shot-Evaluierung verwendet.

| Methode                            | Accuracy |
| ---------------------------------- | -------- |
| CLIP Zero-Shot                     | 85.99 %  |
| ResNet50 (Transfer Learning, Aug.) | 80.4 %   |


---


## 🛠️ Verwendete Bibliotheken

- `torch` ≥ 2.0
- `torchvision`
- `scikit-learn`
- `matplotlib`, `PIL`
- optional: `gradio` für die Space

---

## 📌 Hinweise

- Modell wurde lokal auf CPU/GPU trainiert.
- Gradio-App erlaubt Hochladen von Bildern zur Laufzeit.
- Deployment erfolgt über Hugging Face Spaces.

---

