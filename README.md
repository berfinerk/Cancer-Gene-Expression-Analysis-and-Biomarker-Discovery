# Cancer-Gene-Expression-Analysis-and-Biomarker-Discovery

Machine learning analysis on RNA-Seq gene expression profiles for cancer classification and genomic biomarker discovery.

---

## 🧬 Proje Hakkında

Bu proje, **Golub et al. (1999)** tarafından yayınlanan biyoinformatik veri setini kullanarak **Akut Lenfoblastik Lösemi (ALL)** ve **Akut Miyeloid Lösemi (AML)** hastalarının gen ekspresyon profillerinden sınıflandırılmasını hedeflemektedir.

Yüksek boyutlu (7.129 gen) mikroarray verisi üzerinde veri sızıntısı (data leakage) engellenerek **PCA**, **ANOVA F-Score Feature Selection** ve **Makine Öğrenmesi Sınıflandırma Modelleri** uygulanmıştır.

---

## 📊 Proje Özet Bulguları & Performans

| Model | Accuracy | ROC-AUC | Öne Çıkan Özellik |
| :--- | :---: | :---: | :--- |
| **Logistic Regression** | **%97.1** | **1.000** | En yüksek doğruluk ve kusursuz sınıf ayrımı |
| **Support Vector Machine (SVM)** | **%94.1** | **0.961** | Yüksek boyutlu uzayda güçlü genelleştirme |
| **Random Forest** | **%88.2** | **0.986** | Karar ağaçları tabanlı tutarlı performans |

---

## 🛠️ Metodoloji ve İş Hattı (Pipeline)

1. **Veri Ön İşleme & Standartlaştırma (StandardScaler):**
   * Veri sızıntısını önlemek için ölçeklendirme sadece Train kümesi ($X_{train}$) üzerinde `fit` edilip Test kümesine `transform` edilmiştir.
2. **2D Boyut İndirgeme & Görselleştirme (PCA):**
   * 7.129 boyutlu veri 2 ana bileşene (PC1 & PC2) indirgenerek hastaların biyolojik ayrışması görselleştirilmiştir.
3. **Özellik Seçimi (ANOVA F-Score - SelectKBest):**
   * Sınıflar arası varyansı en yüksek olan **Top 50 biyomarker gen** seçilmiştir.
4. **Model Eğitimi & Değerlendirme:**
   * Confusion Matrix, Precision, Recall, F1-Score ve ROC-AUC metrikleri ile modeller kıyaslanmıştır.
5. **Klinik Biyomarker Analizi (Feature Importance):**
   * Model katsayıları analiz edilerek literatürdeki **c-myb (`U22376`)**, **CST3 (`M27891`)** ve **Zyxin (`X95735`)** gibi kritik lösemi biyomarker'larının kararlardaki rolü doğrulanmıştır.

---

## 🚀 Kurulum & Çalıştırma

```bash
# Depoyu klonlayın
git clone [https://github.com/KULLANICI_ADIN/Cancer-Gene-Expression-Analysis-and-Biomarker-Discovery.git](https://github.com/KULLANICI_ADIN/Cancer-Gene-Expression-Analysis-and-Biomarker-Discovery.git)

# Proje dizinine geçin
cd Cancer-Gene-Expression-Analysis-and-Biomarker-Discovery

# Gerekli paketleri yükleyin
pip install -r requirements.txt