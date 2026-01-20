# Loose Coupling in Java and Spring Boot

## What is Loose Coupling?

Loose coupling means that classes depend on **abstractions (interfaces)** rather than concrete implementations. This allows systems to be more **flexible, maintainable, testable, and scalable**.

In simple terms:

> _Change in one class should have minimal or no impact on other classes._

---

## Tight Coupling Example (Bad Practice)

```java
class CreditCardPayment {
    public void process() {
        System.out.println("Credit card payment processed");
    }
}

class PaymentService {
    private CreditCardPayment payment = new CreditCardPayment();

    public void pay() {
        payment.process();
    }
}
```

```
interface Payment {
    void process();
}

class CreditCardPayment implements Payment {
    public void process() {
        System.out.println("Credit card payment");
    }
}

class PaymentService {
    private Payment payment;

    public PaymentService(Payment payment) {
        this.payment = payment;
    }

    public void pay() {
        payment.process();
    }
}
```

## What is a Dependency?

> A dependency is any object, class, or service that another class needs to function.If a class uses another class to do its work, it depends on it.
