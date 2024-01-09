# enoca-proje
# Challenge
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;
import java.util.Random;









public class Main {
    public static void main(String[] args) {
        
        // 1. Adım: 100 adet random sayıya sahip bir liste oluşturun
        List<Integer> originalList = generateRandomList(100);

        // 2. Adım: Listenin bir kopyasını oluşturun
        List<Integer> copyList = new ArrayList<>(originalList);

        // 3. Adım: 0 ile 100 arasında rastgele bir sayı üretin
        Random random = new Random();
        int randomIndex = random.nextInt(100);

        // 4. Adım: Kopya listedeki bu random sayının olduğu indisteki değeri silin
        copyList.remove(randomIndex);

        // 5. Adım: Hangi elemanın eksik olduğunu bulan metot
        int missingElement = findMissingElement(originalList, copyList);

        // Sonuçları ekrana yazdır
        System.out.println("Orijinal Liste: " + originalList);
        System.out.println("Kopya Liste: " + copyList);
        System.out.println("Eksik Eleman: " + missingElement);
    }

    // Metot: Hangi elemanın eksik olduğunu bulan metot
    private static int findMissingElement(List<Integer> originalList, List<Integer> copyList) {
        Collections.sort(originalList);
        Collections.sort(copyList);

        for (int i = 0; i < originalList.size(); i++) {
            if (!originalList.get(i).equals(copyList.get(i))) {
                return originalList.get(i);
            }
        }

        // Eğer buraya kadar gelinirse, listenin son elemanı eksiktir.
        return originalList.get(originalList.size() - 1);
    }

    // Metot: Belirtilen sayıda random sayı içeren bir liste oluşturur
    private static List<Integer> generateRandomList(int size) {
        List<Integer> randomList = new ArrayList<>();
        Random random = new Random();

        for (int i = 0; i < size; i++) {
            randomList.add(random.nextInt(101)); // 0 ile 100 arasında random sayı üret
        }

        return randomList;
    }
}
