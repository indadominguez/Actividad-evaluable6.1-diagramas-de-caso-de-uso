# Descripción
## La actividad consiste en:

**Tras la reunión del analista, recibes una lista de Requisitos Funcionales para implementar el funcionamiento de un cajero de banco:**
- R1. El cliente debe validarse en el sistema para poder realizar cualquier operación en el cajero automático.
- R2. Si el cliente intenta sacar una cantidad que supera el saldo de su cuenta, el cajero le avisará de que no es posible sacar esa cantidad
- R3. Si el cliente intenta sacar una cantidad que supera el límite diario, el cajero le avisará de que no es posible y volverá a solicitar una cantidad
- R4. El cliente podrá hacer una transferencia a otra cuenta
- R5. El cliente podrá realizar un ingreso a través del cajero automático

Representa mediante una diagrama de casos de uso, los distintos escenarios, actores y relaciones.

**Objetivo:**

- Conocer los diagramas de casos de uso y sus elementos.
- Describir escenarios, detallando los casos de uso.

**Trabajo a realizar:**

- Crea el diagrama de uso haciendo uso de platuml, representado los actores y casos de uso que identifiques en los requisitos.
- Describe, haciendo uso de la plantilla, al menos el caso de uso "Sacar dinero", con las interacciones que tiene entre el actor y el caso de uso.
- Responde a las siguiente pregunta: ¿Para qué me sirve tener/realizar un diagrama de casos de uso modelando el sistema que se representa? ¿Qué aporta?
# 1. Crea el diagrama de uso haciendo uso de platuml, representado los actores y casos de uso que identifiques en los requisitos.
![image](https://github.com/user-attachments/assets/d61f5857-8298-4356-90da-31661dce6352)

# 2. Describe, haciendo uso de la plantilla, al menos el caso de uso "Sacar dinero", con las interacciones que tiene entre el actor y el caso de uso.
## Caso de Uso: Validarse en el sistema
- ID: UC1
- Actores Primarios: Cliente
- Actores Secundarios: Cajero
- Descripción:
  - El cliente debe autenticarse en el sistema para acceder a cualquier otra funcionalidad del cajero automático.

**Precondiciones:**

- El cliente debe tener una tarjeta y un PIN válido.
- Flujo Básico:
  - Cliente inserta la tarjeta en el cajero.
  - El Cajero solicita el PIN.
  - Cliente introduce el PIN.
  - El Cajero valida el PIN y, si es correcto, otorga acceso al menú principal de operaciones.
  
**Postcondiciones:**

- El Cliente tiene acceso al menú de operaciones del cajero automático.
- Excepciones:
  - Si el PIN es incorrecto, el Cajero muestra un mensaje de error y solicita que se ingrese nuevamente.
  - Después de tres intentos fallidos, el Cajero bloquea temporalmente la cuenta o solicita ayuda al personal del banco.

## Caso de Uso: Sacar dinero
- ID: UC2
- Actores Primarios: Cliente
- Actores Secundarios: Cajero
- Descripción:
  - El cliente puede retirar dinero de su cuenta, sujeto a que tenga suficiente saldo y no haya superado su límite diario de retiro.

**Precondiciones:**

- El cliente debe haber sido validado en el sistema.
- Flujo Básico:
  - Cliente selecciona la opción "Sacar dinero".
  - El Cajero solicita la cantidad a retirar.
  - Cliente introduce la cantidad deseada.
  - El Cajero verifica si el saldo es suficiente.
  - Si el saldo es insuficiente, se activa el flujo alternativo.
  - El Cajero verifica si el límite diario ha sido alcanzado.
  - Si el límite diario es alcanzado, se activa el flujo alternativo.
  - Si ambas verificaciones son satisfactorias, el Cajero realiza el retiro y entrega el dinero al Cliente.
  - El Cajero muestra un mensaje de confirmación.
    
**Postcondiciones:**

- El saldo de la cuenta del cliente se actualiza y refleja la cantidad retirada.
- Flujo Alternativo (Saldo insuficiente):
  - Si el saldo es insuficiente, el Cajero muestra un mensaje de error y solicita al Cliente que ingrese una cantidad menor.
- Flujo Alternativo (Límite diario alcanzado):
  - Si el límite diario es alcanzado, el Cajero muestra un mensaje de error y solicita al Cliente que ingrese una cantidad menor.

## Caso de Uso: Transferir dinero
- ID: UC3
- Actores Primarios: Cliente
- Actores Secundarios: Cajero
- Descripción:
  - El cliente puede transferir dinero a otra cuenta, asegurándose de que tenga suficiente saldo.

**Precondiciones:**

- El cliente debe haber sido validado en el sistema.
- Flujo Básico:
  - Cliente selecciona la opción "Transferir dinero".
  - El Cajero solicita el número de cuenta destino y el monto a transferir.
  - Cliente introduce la cuenta destino y la cantidad a transferir.
  - El Cajero verifica si el saldo es suficiente.
  - Si el saldo es insuficiente, se activa el flujo alternativo.
  - El Cajero realiza la transferencia y muestra un mensaje de confirmación.
  
**Postcondiciones**:

- El saldo de la cuenta del cliente se actualiza reflejando la transferencia realizada.
- Flujo Alternativo (Saldo insuficiente):
  - Si el saldo es insuficiente, el Cajero muestra un mensaje de error y solicita al Cliente que ingrese una cantidad menor.
    
## Caso de Uso: Hacer un ingreso
- ID: UC4
- Actores Primarios: Cliente
- Actores Secundarios: Cajero
- Descripción:
  - El cliente puede hacer un ingreso de dinero en su cuenta mediante el cajero automático.

**Precondiciones:**

- El cliente debe haber sido validado en el sistema.
- Flujo Básico:
  - Cliente selecciona la opción "Hacer un ingreso".
  - El Cajero solicita al Cliente que inserte los billetes.
  - Cliente inserta los billetes en la ranura correspondiente.
  - El Cajero cuenta el dinero y muestra un mensaje con el monto ingresado.
  - El Cajero actualiza el saldo de la cuenta del cliente.
  - El Cajero muestra un mensaje de confirmación.
  
**Postcondiciones**:

- El saldo de la cuenta del cliente se actualiza reflejando el monto ingresado.

## Caso de Uso: Ver saldo insuficiente
- ID: UC5
- Actores Primarios: Cajero
- Descripción:
  - Este caso de uso se activa cuando el cliente intenta realizar una operación que excede el saldo disponible en su cuenta.

**Precondiciones**:

- El cliente ha solicitado una operación (como retirar dinero o transferir fondos).
- Flujo Básico:
  - El Cajero verifica el saldo de la cuenta del cliente.
  - Si el saldo es insuficiente, el Cajero muestra un mensaje de error y solicita al Cliente que ingrese una cantidad menor.

**Postcondiciones**:

- No se realiza ninguna transacción si el saldo es insuficiente.

## Caso de Uso: Ver límite diario alcanzado
- ID: UC6
- Actores Primarios: Cajero
- Descripción:
  - Este caso de uso se activa cuando el cliente intenta retirar una cantidad que excede su límite diario de retiro.

**Precondiciones:**

- El cliente ha solicitado un retiro de dinero.
- Flujo Básico:
  - El Cajero verifica si el monto solicitado excede el límite diario de retiro.
  - Si el límite diario ha sido alcanzado, el Cajero muestra un mensaje de error y solicita al Cliente que ingrese una cantidad menor.

**Postcondiciones**:

- No se realiza ninguna transacción si el límite diario es alcanzado.
