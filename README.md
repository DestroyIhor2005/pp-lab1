# pp-lab1
# Main.class
import java.util.Scanner;

public class Main
{
    public static void main(String[] args) {
        int n ;
        System.out.print("Введіть n: ");
        Scanner clava = new Scanner(System.in);// Сканер для вводу інформації у програму

        n = clava.nextInt();// Зчитуємо введене ціле число з клавіатури

        System.out.println("Ви ввели число " + n);

        LukeNumber luke = new LukeNumber();// Створюємо об'єкт (luke) для роботи з числами Люка
        System.out.println("Число Люка з номером " + n + " = " + luke.Calculate(n));

        System.out.println("Перевірка правдивості формули: ");
        // Цикл перевірки справедливості формули для чисел Люка в позиції від 0 до n
        for (int i = 0; i <= n; i++)
        {
            System.out.println(i + ". Число Люка = " + luke.Calculate(i) + "; Правдивість формули : " + luke.Check(i));
        }

    }
}
# LukeNumber.class
public class LukeNumber
{
    public int Calculate(int n) // Метод для обчислення числа Люка у позиції n
    {
        if (n == 0) {
            return 2;
        }
        else
        {
            if (n == 1) {
                return 1;
            }
            else
            {
                return Calculate(n-1) + Calculate(n -2);// Рекурсивний виклик функції для обчислення числа Люка як суми двох попередніх
            }
        }
    }

    public boolean Check(int n)// Перевірка вірності формули для сусідніх чисел Люка n i n + 1
    {
        return  (n * Calculate(n+1) > (n+1) * Calculate(n));
    }
}
