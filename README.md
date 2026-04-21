mvn clean org.jacoco:jacoco-maven-plugin:0.8.11:prepare-agent test org.jacoco:jacoco-maven-plugin:0.8.11:report

FROM eclipse-temurin:17-jdk
COPY . /app
WORKDIR /app
RUN javac hello.java
CMD ["java","hello"]

package com.bnmit;

class BankAccount {
    private double balance;

    public BankAccount(double initialBalance) {
        if (initialBalance < 0) {
            throw new IllegalArgumentException("Initial balance cannot be negative");
        }
        this.balance = initialBalance;
    }

    public void deposit(double amount) {
        if (amount <= 0) {
            throw new IllegalArgumentException("Deposit must be positive");
        }
        balance += amount;
    }

    public void withdraw(double amount) {
        if (amount <= 0 || amount > balance) {
            throw new IllegalArgumentException("Invalid withdrawal");
        }
        balance -= amount;
    }

    public double getBalance() {
        return balance;
    }
}

public class BankService {
    public static void main(String[] args) {
        BankAccount acc = new BankAccount(1000);

        acc.deposit(500);
        acc.withdraw(300);

        System.out.println("Final Balance: " + acc.getBalance());
    }
}

cd target
java -cp sample-app-1.0-SNAPSHOT.jar com.bnmit.BankService

//calculator test program
package com.bnmit;

import static org.junit.jupiter.api.Assertions.*;
import org.junit.jupiter.api.Test;

public class CalculatorTest {

    Calculator calc = new Calculator();

    @Test
    public void testAdd() {
        assertEquals(5, calc.add(2, 3));
    }

    @Test
    public void testDivide() {
        assertEquals(2, calc.divide(4, 2));
    }

    @Test
    public void testDivideByZero() {
        assertThrows(IllegalArgumentException.class, () -> {
            calc.divide(4, 0);
        });
    }

}
//main
package com.bnmit;

public class Calculator {

    // Method for addition
    public int add(int a, int b) {
        return a + b;
    }

    // Method for division
    public int divide(int a, int b) {
        if (b == 0) {
            throw new IllegalArgumentException("Cannot divide by zero");
        }
        return a / b;
    }

    // Optional main method (to run manually)
    public static void main(String[] args) {
        Calculator calc = new Calculator();

        System.out.println("Addition: " + calc.add(2, 3));
        System.out.println("Division: " + calc.divide(4, 2));

        // Uncomment to test exception
        // System.out.println(calc.divide(4, 0));
    }
}
myvolume:/usr/share/nginx/html nginx
myvolume:/data ubuntu bash
cd Desktop
mkdir git-exp5
cd git-exp5
git init

echo "This is version 1" > file.txt

git add file.txt
git commit -m "Initial commit"

git tag v1.0
git tag -a v1.2 -m "v1.2 Created"

git tag
git show v1.0

git remote add origin https://github.com/your-username/git-exp5.git

git push -u origin master
git push --tags
