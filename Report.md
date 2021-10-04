# Отчёт о тестировании функциональности валидации банковских карт

## Краткое описание

04.10.21 - 04.10.21 было проведено функциональное тестирование валидации различных банковских карт.

На тестирование затрачено: 1 час

В результате тестирования выявлены следующие дефекты:
* Дефекты не выявлены.

## Описание процесса тестирования

В процессе тестирования использовались следующие артефакты*:
* IntelliJ IDEA (ПО);
* следующий программный код
```
public class Main {
  public static void main(String[] args) {
    // TODO: подставлять номер карты нужно сюда между двойными кавычками, без пробелов
    String number = "5351719427810741";
    System.out.println(String.format("Result is %s", isValidCardNumber(number) ? "OK" : "FAIL"));
  }

  public static boolean isValidCardNumber(String number) {
    if (number == null) {
      return false;
    }

    if (number.length() != 16) {
      return false;
    }

    long result = 0;
    for (int i = 0; i < number.length(); i++) {
      int digit;
      try {
        digit = Integer.parseInt(number.charAt(i) + "");
      } catch (NumberFormatException e) {
        return false;
      }

      if (i % 2 == 0) {
        digit *= 2;
        if (digit > 9) {
          digit -= 9;
        }
      }
      result += digit;
    }

    return (result != 0) && (result % 10 == 0);
  }
}
```


В качестве тестовых данных использовались данные:
* https://www.freeformatter.com/credit-card-number-generator-validator.html;


Тестирование производилось в следующем окружении:
* Windows 10 Pro, x64;
* Java v 11.0.12;
* IntelliJ IDEA v 2021.2.2
