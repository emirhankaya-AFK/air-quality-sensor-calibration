# English  
## Purpose  
Calibration of low‑cost metal‑oxide gas sensors against certified NO₂ reference measurements using the UCI Air Quality dataset. The workflow focuses on temporal validation, sensor drift, missing measurements, and uncertainty reporting rather than a single shuffled score.  

## Verified Features  
- Uses five sensor responses, temperature, relative/absolute humidity, and cyclical time features.  
- Excludes other certified pollutant reference columns to avoid a misleading calibration task.  
- Imputation + gradient boosting for point predictions.  
- 90 % split‑conformal intervals for uncertainty quantification.  
- Chronological holdout: oldest 80 % for training, next 10 % for interval calibration, newest 10 % locked test.  
- Evaluation metrics on the holdout (772 hourly observations):  
  - MAE = 39.56 µg/m³ (calibrated) vs 44.97 µg/m³ (training‑median baseline)  
  - RMSE = 44.32 µg/m³ (calibrated) vs 55.95 µg/m³ (baseline)  
  - R² = 0.049 (calibrated) vs –0.516 (baseline)  
  - Nominal 90 % conformal interval covers 96.0 % of test observations with a ±73.58 µg/m³ radius.  
- Population Stability Index (PSI) reports drift in humidity, temperature, and the NO₂‑sensitive sensor response.  

## Stack  
- Python (≥3.8)  
- Dependencies managed via `pyproject.toml` (install with `pip install -e ".[dev]"`)  
- Core libraries implied by the codebase: data handling (`pandas`/`numpy`), modeling (gradient boosting), conformal prediction, and testing (`pytest`, `ruff`).  

## Setup & Usage  
```bash
# Install the package in editable mode with development extras
python -m pip install -e ".[dev]"

# Download the UCI Air Quality dataset (checksum recorded in data/manifest.json)
python scripts/download_data.py

# Train the model and produce artifacts
python scripts/train.py

# Generate the holdout calibration plot and metrics (already committed in artifacts/)
```

## Testing  
- Run unit tests: `python -m pytest -q`  
- Check code style: `python -m ruff check .`  
- CI status is reflected by the badge in the repository header.  

## Limitations  
- Data originate from a single device in one Italian city (2004‑2005).  
- Deployment‑specific calibration metadata is limited.  
- Large seasonal shifts violate stationarity assumptions of simple calibration.  
- The model is not suitable for regulatory or health decisions without contemporary co‑location data.  

## License  
Code is available under the MIT License (see `LICENSE`). Dataset rights remain with the original source.  

---  

# Türkçe  
## Amaç  
UCI Air Quality veri seti kullanılarak düşük maliyetli metal‑oksit gaz sensörlerinin sertifikalı NO₂ referans ölçümlerine göre kalibrasyonu. İş akışı, tek bir karıştırılmış skor yerine zaman doğrulaması, sensör drifti, eksik ölçümler ve belirsizlik raporlamasına odaklanır.  

## Doğrulanan Özellikler  
- Beş sensör yanıtı, sıcaklık, görevi/mutlak nem ve döngüsel zaman özellikleri kullanılır.  
- Başka sertifikalı pollutant referans sütunları yanıltıcı bir kalibrasyon görevi oluşturabileceğinden çıkarılır.  
- Nokta tahminleri için eksik veri doldurulması + gradyan artırma modeli.  
- Belirsizlik kuantifikasyonu için %90 bölünmüş‑konformal aralıklar.  
- Kronolojik tutma: en eski %80 eğitim, sonraki %10 interval kalibrasyonu, en yeni %10 kilitli test.  
- Tutma seti (772 saatlik gözlem) üzerindeki değerlendirme metrikleri:  
  - MAE = 39.56 µg/m³ (kalibre) vs 44.97 µg/m³ (eğitim‑medyan baz)  
  - RMSE = 44.32 µg/m³ (kalibre) vs 55.95 µg/m³ (baz)  
  - R² = 0.049 (kalibre) vs –0.516 (baz)  
  - Nominal %90 konformal aralık test gözlemlerinin %96.0’sini kapsar, ±73.58 µg/m³ yarıçap.  
- Popülasyon Stabilite Endeksi (PSI), nem, sıcaklık ve NO₂ duyarlı sensör yanıtındaki drifti raporlar.  

## Yığın (Stack)  
- Python (≥3.8)  
- Bağımlılıklar `pyproject.toml` ile yönetilir (`pip install -e ".[dev]"` ile kurulum)  
- Kod tabanı tarafından öne çıkarılan kütüphaneler: veri işleme (`pandas`/`numpy`), modelleme (gradyan artırma), konformal tahmin ve test (`pytest`, `ruff`).  

## Kurulum & Kullanım  
```bash
# Geliştirme ekstralarıyla düzenlenebilir kurulum
python -m pip install -e ".[dev]"

# UCI Air Quality veri setini indir (checksum data/manifest.json içinde)
python scripts/download_data.py

# Modeli eğit ve artefaktları üret
python scripts/train.py

# Holdout kalibrasyon grafiği ve metrikleri (artifacts/ içinde zaten mevcut)
```

## Test  
- Birim testleri: `python -m pytest -q`  
- Kod stili denetimi: `python -m ruff check .`  
- CI durumu depo başlığındaki rozetle gösterilir.  

## Sınırlamalar  
- Veri tek bir cihazdan, İtalya’nın bir şehrinden (2004‑2005) gelmektedir.  
- Dağıtım‑özgü kalibrasyon meta verisi sınırlıdır.  
- Büyük mevsimsel değişiklikler basit kalibrasyonun durağanlık varsayımını ihlal eder.  
- Model, współ‑lokasyon verisi olmadan düzenleyici veya sağlık kararları için uygun değildir.  

## Lisans  
Kod MIT Lisansı altında sunulmaktadır (`LICENSE` dosyasına bakınız). Veri hakkı orijinal kaynağa aittir.  

---  

# Deutsch  
## Zweck  
Kalibrierung von kostengünstigen Metalloxid‑Gassensoren anhand zertifizierter NO₂‑Referenzmessungen mit dem UCI Air‑Quality‑Datensatz. Der Workflow legt den Fokus auf zeitliche Validierung, Sensordrift, fehlende Messungen und Unsicherheitsquantifizierung anstelle eines einzelnen zufällig gemischten Scores.  

## Verifizierte Eigenschaften  
- Es werden fünf Sensorsignale, Temperatur, relative/absolute Luftfeuchtigkeit und zyklische Zeitmerkmale verwendet.  
- Andere zertifizierte Schadstoffreferenzspalten werden bewusst ausgeblendet, um eine irreführende Kalibrierungsaufgabe zu vermeiden.  
- Punktvorhersagen erfolgen mittels Imputation + Gradient Boosting.  
- Unsicherheit wird durch 90 % split‑konforme Intervalle quantifiziert.  
- Chronologisches Hold‑out: älteste 80 % zum Training, folgende 10 % zur Intervallkalibrierung, neueste 10 % als gesperrter Test.  
- Evaluationsmetriken am Hold‑out (772 stündliche Beobachtungen):  
  - MAE = 39.56 µg/m³ (kalibriert) vs 44.97 µg/m³ (Trainings‑Median‑Baseline)  
  - RMSE = 44.32 µg/m³ (kalibriert) vs 55.95 µg/m³ (Baseline)  
  - R² = 0.049 (kalibriert) vs –0.516 (Baseline)  
  - Das nominale 90 % konforme Intervall deckt 96,0 % der Testbeobachtungen ab mit einem Radius von ±73.58 µg/m³.  
- Der Population Stability Index (PSI) zeigt Drift bei Luftfeuchtigkeit, Temperatur und dem NO₂‑empfindlichen Sensorsignal.  

## Stack  
- Python (≥3.8)  
- Abhängigkeiten werden über `pyproject.toml` verwaltet (Installation mit `pip install -e ".[dev]"`)  
- Die Codebasis impliziert Bibliotheken wie Datenverarbeitung (`pandas`/`numpy`), Modellierung (Gradient Boosting), konforme Vorhersage und Testing (`pytest`, `ruff`).  

## Einrichtung & Nutzung  
```bash
# Paket im editierbaren Modus mit Entwicklungsextras installieren
python -m pip install -e ".[dev]"

# UCI Air‑Quality Datensatz herunterladen (Prüfsumme in data/manifest.json)
python scripts/download_data.py

# Modell trainieren und Artefakte erzeugen
python scripts/train.py

# Hold‑out Kalibrierungsplot und Metriken (bereits im artifacts/‑Ordner vorhanden)
```

## Test  
- Unit‑Tests ausführen: `python -m pytest -q`  
- Stilprüfung: `python -m ruff check .`  
- Der CI‑Status wird durch das Badge im Repository‑Header angezeigt.  

## Einschränkungen  
- Die Daten stammen von einem einzigen Gerät in einer italienischen Stadt (2004‑2005).  
- Einsatzspezifische Kalibrierungsmetadaten sind begrenzt.  
- Große saisonale Veränderungen verletzen die Stationaritätsannahme einfacher Kalibrierungen.  
- Das Modell ist ohne aktuelle Kolokationsdaten nicht für behördliche oder gesundheitsrelevante Entscheidungen geeignet.  

## Lizenz  
Der Code steht unter der MIT‑Lizenz (siehe `LICENSE`). Die Rechte am Datensatz verbleiben beim ursprünglichen Urheber.
