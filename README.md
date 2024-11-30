#Homework8
import logging


logging.basicConfig(
    filename="calculation_errors.log",
    level=logging.ERROR,
    format="%(asctime)s - %(levelname)s - %(message)s",
    filemode="a"  # Дозапис у файл
)

class Calculation:
    def call(self, a, b, operation):
        try:
            
            a = self._convert_to_number(a)
            b = self._convert_to_number(b)

            # Виконання операції
            if operation == "+":
                return a + b
            elif operation == "-":
                return a - b
            elif operation == "*":
                return a * b
            elif operation == "/":
                if b == 0:
                    raise ZeroDivisionError("Ділення на нуль неможливе.")
                return a / b
            else:
                raise ValueError(f"Операція '{operation}' не підтримується.")
        except Exception as e:
            # Логування виключень
            logging.error(f"Помилка виконання операції: {e}")
            raise

    def _convert_to_number(self, value):
        """Метод для перевірки типу і конвертації до int або float."""
        try:
            if isinstance(value, (int, float)):
                return value
            elif isinstance(value, str):
                if "." in value:
                    return float(value)
                else:
                    return int(value)
            else:
                raise TypeError(f"Тип {type(value).name} не підтримується.")
        except Exception as e:
            
            logging.error(f"Помилка конвертації значення '{value}': {e}")
            raise


if name == "main":
    calc = Calculation()
