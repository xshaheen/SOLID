# SOLID Principles

- SOLID is an a mnemonic acronym for five design principles intended to make software designs more understandable.
- These principles aim to make the code more readable, easy to maintain, extensible, reusable and without repetition.
- The principles are a subset of many principles _Robert C. Martin (Uncle Bob)_ in his 2000 paper _Design Principles and Design Patterns_, although the SOLID acronym was introduced later by _Michael Feathers_.

---

- **S** - Single-responsiblity principle
- **O** - Open-closed principle
- **L** - Liskov substitution principle
- **I** - Interface segregation principle
- **D** - Dependency Inversion Principle

---

- **Single Responsibility Principle**

  **A class must have only one reason to change and only one responsibility.**

  ### Bad

  ```csharp
  public sealed class Invoice
  {
      public int Id { get; set; }

      public double Price { get; set; }

        public float TaxPercentage { get; set; }

        public double GetTaxAmount()
        {
          return Price * TaxPercentage / 100;
        }

      public void Insert()
      {
        /// Implementation for ADDING to DATABASE
      }

      public void Delete()
      {
        /// Implementation for DELETING to DATABASE
      }
  }
  ```

  **The code is incorrect because it has two responsibilities, business rules and database persistence.**

  ### Good

  ```csharp
  public sealed class Invoice
  {
      public int Id { get; set; }

      public double Price { get; set; }

        public float TaxPercentage { get; set; }

        public double GetTaxAmount()
        {
            return Price * TaxPercentage / 100;
        }
  }
  ```

  ```csharp
  public sealed class InvoiceRepository
  {
      public void Insert(Customer customer)
      {
          /// Implementation for ADDING to DATABASE
      }

      public void Delete(Customer customer)
      {
          /// Implementation for DELETING to DATABASE
      }
  }
  ```

  **The code is correct because the responsibilities have been split, and each class has only one reason to change.**
