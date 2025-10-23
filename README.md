# UstaPlatform01
# UstaPlatform - Şehrin Uzmanlık Platformu

## 📋 Proje Hakkında
Arcadia şehrindeki kayıp uzmanları vatandaş talepleriyle eşleştiren, dinamik fiyatlama ve akıllı rota planlama yapabilen genişletilebilir bir platform.

## 🚀 Kurulum ve Çalıştırma

### Gereksinimler
- .NET 8.0 SDK veya üzeri
- Visual Studio 2022 veya VS Code

### Kurulum Adımları
1. Projeyi klonlayın veya zip dosyasını çıkarın
2. `UstaPlatform.sln` dosyasını Visual Studio'da açın
3. Solution'ı build edin: `Build > Build Solution`
4. Ana proje olarak `UstaPlatform.App`'i seçin
5. Uygulamayı çalıştırın: `Debug > Start Without Debugging`

### Demo Çalıştırma
1. Uygulamayı çalıştırın - temel senaryo otomatik çalışacaktır
2. DLL eklentisi testi için:
   - `LoyaltyDiscountRule.dll` dosyasını `UstaPlatform.App/bin/Debug/net8.0/` klasörüne kopyalayın
   - Uygulamayı yeniden çalıştırın

## 🏗️ Tasarım Kararları ve Mimari

### Katmanlı Mimari
Proje, SOLID prensiplerine uygun 4 katmandan oluşur:

1. **Domain Katmanı**: Core entity'ler (Master, Citizen, Request, WorkOrder)
2. **Pricing Katmanı**: Fiyatlandırma kuralları ve motoru
3. **Infrastructure Katmanı**: Yardımcı sınıflar ve özel koleksiyonlar
4. **App Katmanı**: Ana uygulama ve iş akışı

### SOLID Prensipleri Uygulamaları

#### 1. Açık/Kapalı Prensibi (OCP)
```csharp
public interface IPricingRule
{
    decimal Apply(decimal basePrice, WorkOrder workOrder);
}
