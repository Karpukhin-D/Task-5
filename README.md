# Практическая работа №5: Практическая работа №5: Одномерные массивы в C#, класс System.Array и модульная консольная RPG
# Спасатели МЧС (Техногенная катастрофа)
## Выполнили студенты группы П25-2.1 Карпухин Дмитрий и Есин Данила
---
<picture>
  <img src="https://github.com/Karpukhin-D/Task-5/blob/main/1.png">
</picture>


<picture>
  <img src="https://github.com/Karpukhin-D/Task-5/blob/main/2.png">
</picture>

```csharp
using System;

class Program
{
    static void Main()
    {
        string[] equipment = { "Гидравлические ножницы", "Дыхательный аппарат", "Пенообразователь", "Носилки", "Дозиметр" };

        string[] dangers = { "Очаг открытого пламени", "Завал перекрытий", "Резервуар с хлором" };
        int[] dangerHp = { 35, 70, 135 };

        int[] workshop = { 1, 2, 3 };
        int[] gasLevels = { 40, 75, 95 };  // Массив уровней загазованности трех цехов
        bool[] explosionRisk = { false, true, true }; // Массив наличия риска взрыва для трех цехов

        int[] survivorsCount = { 3, 5, 2, 4 }; // Число спасенных людей в четырех отсеках

        int[] ppmLog = { 120, 350, 210, 480, 290 }; // Массив из пяти контрольных измерений токсичных паров


        Console.WriteLine("=== СПАСАТЕЛИ МЧС ===");
        Console.WriteLine("Ликвидация техногенной катастрофы");
        Console.WriteLine();

        Console.WriteLine("Опасности на территории:");

        for (int i = 0; i < dangers.Length; i++) // Повторяем действия для каждой опасности в массиве
        {
            Console.WriteLine($"{dangers[i]} — {dangerHp[i]} HP"); // Выводим название опасности и соответствующее ей здоровье
        }

        Console.WriteLine();

        Console.WriteLine("Доступное оборудование:");

        foreach (string item in equipment)
        {
            Console.WriteLine($"- {item}");
        }

        Console.WriteLine();

        string neededEquipment = "Гидравлические ножницы";
        int equipmentIndex = Array.IndexOf(equipment, neededEquipment); // Array.IndexOf ищет предмет в массиве и возвращает его индекс.

        if (equipmentIndex != -1)
        {
            Console.WriteLine($"Оборудование найдено: {neededEquipment}");
            Console.WriteLine("Можно приступать к резке балки.");
        }
        else
        {
            Console.WriteLine($"Оборудование отсутствует: {neededEquipment}");
            Console.WriteLine("Резка балки невозможна.");
        }

        Console.WriteLine();

        Console.WriteLine("Информация об аварийных секторах:");

        for (int i = 0; i < workshop.Length; i++)
        {
            string risk; 

            if (explosionRisk[i] == true) // проверяем значение риска для текущего цеха
            {
                risk = "Есть";
            }
            else
            {
                risk = "Нет";
            }

            Console.WriteLine($"Цех {workshop[i]}: загазованность {gasLevels[i]}%, риск взрыва: {risk}");
        }

        Console.WriteLine();

        int totalSurvivors = 0; //общее количество спасенных людей

        for (int i = 0; i < survivorsCount.Length; i++)
        {
            totalSurvivors = totalSurvivors + survivorsCount[i];
        }

        Console.WriteLine($"Всего спасено людей: {totalSurvivors}");

        Console.WriteLine();

        int maxPpm = ppmLog[0]; // Считаем, что первый замер пока является максимальным
        int maxPpmIndex = 0; // Запоминаем индекс первого замера

        for (int i = 1; i < ppmLog.Length; i++)  // начинаем с индекса 1, т.к. элемент с индексом 0 уже выбран как начальный максимум
        {
            if (ppmLog[i] > maxPpm) // Сравниваем текущий замер с найденным максимумом
            {
                maxPpm = ppmLog[i]; // Если нашли большее значение, обновляем максимум.
                maxPpmIndex = i;
            }
        }

        Console.WriteLine($"Максимальная концентрация токсичных паров: {maxPpm} ppm");
        Console.WriteLine($"Номер контрольного замера: {maxPpmIndex + 1}");

        Console.WriteLine();

        Array.Sort(ppmLog);

        Console.WriteLine("Замеры ppm по возрастанию:");

        for (int i = 0; i < ppmLog.Length; i++) // перебираем отсортированный массив по индексам
        {
            Console.WriteLine($"{i + 1}. {ppmLog[i]} ppm"); // Выводим порядковый номер замера и его значение
        }

        Console.WriteLine();

        Array.Resize(ref equipment, 7);

        equipment[5] = "Защитные костюмы";
        equipment[6] = "Газоанализатор";

        Console.WriteLine("Оборудование после прибытия спецтехники:");

        foreach (string item in equipment)
        {
            Console.WriteLine($"- {item}");
        }

        Console.WriteLine();
        Console.WriteLine("Работа спасательного отряда завершена.");
    }
}
```
