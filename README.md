# odev-6
odev 6
import java.util.Random;
import java.util.Scanner;
public class adamasmaoyunu {
    public static void main(String[] args) {
        String[] sehirler = {"Ankara", "Adıyaman", "Tokat", "Bursa", "Adana", "Antalya", "Eskişehir",
                "Balıkesir", "Gaziantep", "Samsun"};
        Random random = new Random();
        // to Upper fonksiyonunu internetten aldım,rastgele şehir seçeceğimiz için de randomu kullanıyoruz.
        String secilenSehir = sehirler[random.nextInt(sehirler.length)].toUpperCase();
        // istenilen bir şehir seçilir ve ekrana yazılır

        char[] tahminArray = new char[secilenSehir.length()];
        for (int i = 0; i < secilenSehir.length(); i++) {
            tahminArray[i] = '_';
        }
        Scanner scanner = new Scanner(System.in);
        long baslangicZamani = System.currentTimeMillis();
        System.out.println("!!! adam asmaca oyunu başlıyor !!!");
        while (true) {
            System.out.println("Tahmin: " + String.valueOf(tahminArray));
            System.out.print("Lütfen tahmin ettiğiniz şehrin herhangi bir harfini giriniz:   ");
            String kullaniciTahmini = scanner.nextLine().toUpperCase();
            // tahminin doğru olup olmadığını kontrol edelim
            boolean dogruTahmin = false;
            for (int i = 0; i < secilenSehir.length(); i++) {
                if (secilenSehir.charAt(i) == kullaniciTahmini.charAt(0)) {
                    tahminArray[i] = kullaniciTahmini.charAt(0);
                    dogruTahmin = true;
                }
            }
            if (!dogruTahmin) {
                System.out.println("Yanlış tahmin!");
            }
            // adam asmacanın bittiğinin kontrolünü yapalım
            if (String.valueOf(tahminArray).equals(secilenSehir)) {
                long bitisZamani = System.currentTimeMillis();
                long sure = (bitisZamani - baslangicZamani) / 1000; // Saniye cinsinden süre hesapla
                int puan = (sure <= 20) ? 100 : ((sure <= 30) ? 90 : 0);
                System.out.println("Tebrikler! Doğru tahmin!. Puanınız: " + puan);
                break;
            }
        }
    }
}
