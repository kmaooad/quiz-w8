# Quiz

## Q1

**What is the issue with this code:**

```csharp
public class List<T> {
    public virtual bool Contains<T>(T element) { ... }
    public virtual void Add<T>(T element) { ... }
}

public class Set<T>: List<T> {
    public override void Add<T>(T element) {
        if (this.Contains(element)) {
             throw new Exception("Set already contains this element");
        }
        base.Add(element);
    }
}
```

a. SRP violation

b. LSP violation

c. Tight coupling

d. Bad DI

e. Bad abstration

## Q2

**What is the issue with this code:**

```csharp
public class Order {
    ...
    public OrderStatus Status { get; set; }
    public void CalculateTotal() { ... }
    ...
}
```

a. DIP violation

b. LSP violation

c. Low cohesion

d. OCP violation

e. Bad encapsulation

## Q3

**What dependency is acceptable:**

```csharp
public class OrderModel { ... }
public class OrderDbContext { ... }
```

a. OrderModel -> OrderDbContext

b. OrderDbContext -> OrderModel

c. Both

d. None

## Q4

**What coupling strength is preferred:**

a. Tight

b. Loose

c. Doesn't matter

## Q5

**What is the _server_ in this code:**

```csharp
public class OrderService: IOrderService {
    public OrderService(OrderContext db) { ... }
}
```

a. OrderService

b. IOrderService

c. OrderContext

d. All

e. None

## Q6

**What issues are present in this code (choose all that apply):**

```csharp
public class Order {
    public void ProcessOrder() {
        using (var db = new OrderContext()){
            var discounts = db.Discounts.Where(...).ToList();
            foreach (var d in discounts) {
                d.ApplyTo(order);
            }
        }
    }
}
```

a. SRP violation

b. OCP violation

c. LSP violation

d. ISP violation

e. DIP violation

## Q7

**What is constructor DI:**

a. `public OrderService(OrderContext db) { ... }`

b. `public void Calculate(OrderContext db) { ... }`

c. `using (var db = new OrderContext()) { ... }`

d. `public class OrderContext: DbContext { ... }`

e. `public class OrderContext: IOrderContext { ... }`

f. All

g. None

## Q8

**Which class is the _client_ in this fragment:**

```csharp
public class CancelledOrder: Order {
    public Reason CancellationReason { get; }
    public Order Resubmit(User initiator) { ... }
    ...
}
```

a. CancelledOrder

b. Order

c. Reason

d. User

e. All

f. None

## Q9

**How many dependencies does CancelledOrder have:**

```csharp
public class CancelledOrder: Order {
    public Reason CancellationReason { get; }
    public Order Resubmit(User initiator) { ... }
    ...
}
```

a. 0

b. 1

c. 3

d. 4

e. 7

f. 11

## Q10

**Does this code meet OCP requirements:**

```csharp
public class OrderService: IOrderService {
    private readonly IDiscountManager _mgr;
    public OrderService(IDiscountManager mgr) { ... }
    public virtual Order Process(ShoppingCart cart){ ... }
}
```

a. Yes

b. No

c. This is not a proper example for OCP