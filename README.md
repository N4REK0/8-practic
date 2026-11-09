# Практическая работа №8
## Выполнили студенты группы П25-2.1. Оганджанян Нарек Артёмикович
## Тема: Вариант 24. Управление микроклиматом винного погреба
### Рекурсия: Рекурсивный расчет испарения вина через дубовую бочку за годы выдержки («доля ангелов») CalculateAngelsShare(double currentLiters, double yearlyLossPercent, int yearsLeft).

<picture> <img src="скрины 8/1.png"> 
</picture>


``` csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace _8
{
    internal class Program
    {
        static double CalculateAngelShare(double currentLiters, double yearlyLossPercent, int yearsLeft)
        {
            if (yearsLeft <= 0)
            {
                return currentLiters;
            }

            double newLiters = currentLiters * (1 - yearlyLossPercent / 100.0);

            return CalculateAngelShare(newLiters, yearlyLossPercent, yearsLeft - 1);
        }

        static void Main(string[] args)
        {
            double startLiters = 100.0;
            double lossPercent = 2.0;
            int years = 5;

            double result = CalculateAngelShare(startLiters, lossPercent, years);

            Console.WriteLine($"Начальный объем вина: {startLiters} литров");
            Console.WriteLine($"Ежегодный процент испарения: {lossPercent}%");
            Console.WriteLine($"Количество лет: {years}");
            Console.WriteLine($"Остаток вина: {result:F0} литров");
        }
    }
}
```
