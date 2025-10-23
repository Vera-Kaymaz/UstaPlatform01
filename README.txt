UstaPlatform - �ehrin Uzmanl�k Platformu

Proje Tan�m�: UstaPlatform, Arcadia �ehrindeki vatanda�lar�n ihtiya� duydu�u ustalar� bulmalar�n� kolayla�t�ran bir sistemdir.
Uygulama, talep ile uzman� otomatik e�le�tirir, fiyat� dinamik �ekilde belirler ve rota planlamas� yapar.

Kurulum Ad�mlar�

1. Proje klas�r�n� indirin veya klonlay�n.
2. `UstaPlatform.sln` dosyas�n� Visual Studio�da a��n.
3. Men�den **Build > Build Solution** ile derleme i�lemini yap�n.
4. Ana ba�lang�� projesi olarak `UstaPlatform.App`�i se�in.
5. **Debug > Start Without Debugging** ile uygulamay� ba�lat�n.

Demo �al��t�rma

1. Uygulama �al��t���nda �rnek senaryo otomatik olarak ba�lar.
2. Eklenti (plugin) testi yapmak i�in:

   * `LoyaltyDiscountRule.dll` dosyas�n� `UstaPlatform.App/bin/Debug/net8.0/` klas�r�ne kopyalay�n.
   * Uygulamay� yeniden ba�lat�n.

Proje Mimarisi

Katmanl� Mimari Yap�s�

Proje 4 ana katmandan olu�ur ve SOLID prensiplerine uygundur:

1. **Domain Katman�:** Temel varl�klar (`Master`, `Citizen`, `Request`, `WorkOrder`)
2. **Pricing Katman�:** Fiyatland�rma kurallar� ve hesaplama motoru
3. **Infrastructure Katman�:** Yard�mc� s�n�flar, �zel koleksiyonlar
4. **App Katman�:** Ana uygulama ak��� ve kullan�c� etkile�imi

SOLID Prensiplerinden �rnek

A��k/Kapal� Prensibi (OCP): Yeni fiyatland�rma kurallar� eklenebilir, mevcut kod de�i�tirilmez:

public interface IPricingRule
{
    decimal Apply(decimal basePrice, WorkOrder workOrder);
}

