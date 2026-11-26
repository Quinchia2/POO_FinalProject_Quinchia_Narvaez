# Smart Parking System - Final Project POO

## Integrantes 
* **Daniel Sebastian Narvaez Muñoz** - Código: `75276` - Github: `@DanielSebastianN`
* **David Quinchia Morcillo** - Código: `75456` - Github: `@Quinchia2`

## Descripción general del sistema
Este sistema de gestión interna diseñado para que los operadores y administradores de un parqueadero automaticen y controlen las operaciones diarias del garaje. Desarrollado bajo los principios de la programación orientada a objetos en java, el sistema gestiona la asignación de espacios, la emisión de tiquetes al ingresar un vehículo, el cálculo dinámico de tarifas y la generación de recibos de pago a la salida.

## Instrucciones de ejecución 
### Prerrequisitos 
* **Java development kit (JDK 25 LTS)** o superior instalado.
* **Git** instalado para la gestión del repositorio.

---

### Pasos para ejecutar 

1. **Clonar el repositorio**:
   ```bash
   git clone https://github.com/Quinchia2/POO_FinalProject_Quinchia_Narvaez
   cd POO_FinalProject_Quinchia_Narvaez
   ```

2. **Compilar el código fuente**:
   ```bash
   javac -d bin src/**/*.java
   ```

3. **Ejecutar el sistema**:
   ```bash
   java -cp bin ui.Main
   ```
---

## Ejemplo de entrada / salida

```text
---Smart parking system - Main menu---
1. Register vehicle entry
2. Process vehicle exit & payment
3. View occupied parking spots
4. Generate csv daily report
5. Exit system
Select an option: 1

--Vehicle entry registration--
Enter license plate: ABC-123
Enter brand: Tesla
Enter color: Red
Select vehicle type (1. Car, 2. Motorcycle, 3. Electric vehicle): 3
Is charging required? (true/false): true

[Decision support] Optimal spot found: Spot E-02 (Electric charging station)
Ticket T-1001 Issued successfully
Entry time: 2026-11-22 14:00

---Smart parking system - Main menu---
1. Register vehicle entry
2. Process vehicle exit & payment
3. View occupied parking spots
4. Generate csv daily report
5. Exit system
Select an option: 2

--Vehicle exit & payment--
Enter ticket ID or license plate: ABC-123
Entry time: 2026-11-22 14:00
Exit time: 2026-11-22 16:30
Total duration: 2 hours 30 mins (Billed as 3 hours)
Vehicle Type: Electric vehicle (Base rate: $5.000/h x 1.2 multiplier)

Total fee calculated: $18.000
Select payment method (1. Cash, 2. Credit card, 3. Transfer): 2
Processing payment... Succes
Spot E-02 is now VACANT
Receipt PAY-5001 generated succesfully
```

---

## Diagrama de clases
```mermaid
classDiagram
    direction TB
    class Vehicle {
        <<abstract>>
        #String licensePlate
        #String brand
        #String color
        +Vehicle()
        +getLicensePlate() String
        +setLicensePlate(String licensePlate) void
        +getBrand() String
        +setBrand(String brand) void
        +getColor() String
        +setColor(String color) void
    }

class Car {
        -int doorsQuantity
        +Car()
        +getDoorsQuantity() int
        +setDoorsQuantity(int doorsQuantity) void
    }

class Motorcycle {
        -boolean helmetLockerRequested
        +Motorcycle()
        +hasHelmetLockerRequested() boolean
        +setHelmetLockerRequested(boolean requested) void
    }

class ElectricVehicle {
        -boolean requiresCharging
        +ElectricVehicle()
        +requiresCharging() boolean
        +setRequiresCharging(boolean charging) void
    }

class ParkingSpot {
        -String spotId
        -String spotType
        -boolean occupied
        -boolean isWide
        +ParkingSpot()
        +isOccupied() boolean
        +setOccupied(boolean occupied) void
        +isWide() boolean
    }

class ParkingTicket {
       -String ticketId
       -LocalDateTime entryTime
       -LocalDateTime exitTime
       -String status
       -double totalFee
       +ParkingTicket()
       +calculateDurationInHours() double
       +calculateTotalFee() double
       +generatePayment() Payment
   }

class Customer {
       -String customerId
       -String name
       -String email
       +Customer()
       +getCustomerId() String
       +getName() String
       +getEmail() String
   }

class Payment {
       -String paymentId
       -double amount
       -LocalDateTime paymentDate
       -String paymentMethod
       +Payment()
       +getPaymentId() String
       +getAmount() double
       +getPaymentDate() LocalDateTime
       +setPaymentMethod(String method) void
   }

class ParkingLot {
       -String name
       -double hourlyRate
       -List~ParkingSpot~ spots
       -List~ParkingTicket~ tickets
       -List~Customer~ customers
       -List~Payment~ payments
       +ParkingLot()
       +addSpot(ParkingSpot spot) void
       +registerCustomer(Customer customer) void
       +issueTicket() ParkingTicket
       +processPayment() Payment
       +findOptimalSpot() ParkingSpot
       +calculateOccupancyRate() double
   }
   Vehicle <|-- Car
   Vehicle <|-- Motorcycle
   Car <|-- ElectricVehicle

   ParkingLot "1" *-- "*" ParkingSpot : manages
   ParkingLot "1" *-- "*" ParkingTicket : registers
   ParkingLot "1" *-- "*" Payment : collects
   ParkingLot "1" *-- "*" Customer : stores

   ParkingTicket "*" --> "1" Vehicle : vehicle
   ParkingTicket "*" --> "1" ParkingSpot : spot
   ParkingTicket "*" --> "1" Customer : customer
   ParkingTicket "1" --> "0..1" Payment : payment
```
