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
```

---

## Diagrama de clases

```mermaid
