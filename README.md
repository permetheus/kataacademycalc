import java.util.Scanner;

public class Calc {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Введите пример в одну строку используя числа от 1 до 10: ");
        String expression = scanner.nextLine();

        try {
            int result = evaluateExpression(expression);
            System.out.println("Результат: " + result);
        } catch (IllegalArgumentException e) {
            System.out.println("Ошибка: " + e.getMessage());
        }
    }

    public static int evaluateExpression(String expression) throws IllegalArgumentException {
        String[] tokens = expression.split(" ");

        if (tokens.length != 3) {
            throw new IllegalArgumentException("Ошибка");
        }

        int a = Integer.parseInt(tokens[0]);
        int b = Integer.parseInt(tokens[2]);
        String operator = tokens[1];

        if (a < 1 || a > 10 || b < 1 || b > 10) {
            throw new IllegalArgumentException("Калькулятор использует числа от 1 до 10");
        }

        int result;

        switch (operator) {
            case "+":
                result = a + b;
                break;
            case "-":
                result = a - b;
                break;
            case "*":
                result = a * b;
                break;
            case "/":
                result = a / b;
                break;
            default:
                throw new IllegalArgumentException("Ошибка");
        }

        return result;
    }
}
