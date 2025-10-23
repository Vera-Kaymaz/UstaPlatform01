UstaPlatform - Þehrin Uzmanlýk Platformu

Proje Tanýmý: UstaPlatform, Arcadia þehrindeki vatandaþlarýn ihtiyaç duyduðu ustalarý bulmalarýný kolaylaþtýran bir sistemdir.
Uygulama, talep ile uzmaný otomatik eþleþtirir, fiyatý dinamik þekilde belirler ve rota planlamasý yapar.

Kurulum Adýmlarý

1. Proje klasörünü indirin veya klonlayýn.
2. `UstaPlatform.sln` dosyasýný Visual Studio’da açýn.
3. Menüden **Build > Build Solution** ile derleme iþlemini yapýn.
4. Ana baþlangýç projesi olarak `UstaPlatform.App`’i seçin.
5. **Debug > Start Without Debugging** ile uygulamayý baþlatýn.

Demo Çalýþtýrma

1. Uygulama çalýþtýðýnda örnek senaryo otomatik olarak baþlar.
2. Eklenti (plugin) testi yapmak için:

   * `LoyaltyDiscountRule.dll` dosyasýný `UstaPlatform.App/bin/Debug/net8.0/` klasörüne kopyalayýn.
   * Uygulamayý yeniden baþlatýn.

Proje Mimarisi

Katmanlý Mimari Yapýsý

Proje 4 ana katmandan oluþur ve SOLID prensiplerine uygundur:

1. **Domain Katmaný:** Temel varlýklar (`Master`, `Citizen`, `Request`, `WorkOrder`)
2. **Pricing Katmaný:** Fiyatlandýrma kurallarý ve hesaplama motoru
3. **Infrastructure Katmaný:** Yardýmcý sýnýflar, özel koleksiyonlar
4. **App Katmaný:** Ana uygulama akýþý ve kullanýcý etkileþimi

SOLID Prensiplerinden Örnek

Açýk/Kapalý Prensibi (OCP): Yeni fiyatlandýrma kurallarý eklenebilir, mevcut kod deðiþtirilmez:

public interface IPricingRule
{
    decimal Apply(decimal basePrice, WorkOrder workOrder);
}

