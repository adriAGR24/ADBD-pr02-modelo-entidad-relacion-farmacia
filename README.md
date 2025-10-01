# Modelo Entidad/Relación: Farmacia

* **Alumno:** Adrián García Rodríguez
* **Correo:** alu0101557977@ull.edu.es

## Descripción de las entidades

- **Medicamento:** representa cada producto farmacéutico gestionado por la farmacia.
  - **Medicamento Fabricado:** producto farmacéutico fabricado por la propia farmacia.
  - **Medicamento Comprado:** producto farmacéutico comprado a terceros (laboratorios).
- **Familia de Medicamentos:** familia que agrupa medicamentos con características comunes.
- **Tipo Enfermedad:** representa una categoría o clasificación de enfermedades dentro del sistema de la farmacia.
- **Laboratorio:** empresa fabricante de medicamentos.
- **Cliente:** persona que realiza compras en la farmacia.
  - **Cliente Común:** cliente que no tiene trato especial en cuanto a pagos (cuando compra un medicamento, lo paga al instante).
  - **Cliente con Crédito:** cliente que realiza los pagos de sus compras a fin de cada mes.

## Descripción y ejemplos de los atributos

### Medicamento

- **Código Medicamento:** identificador único del medicamento.
  - **Dominio:** cadena alfanumérica de longitud fija o variable, sin repeticiones.
  - **Ejemplos:** `MED001`, `A123B`.

- **Nombre Medicamento:** nombre comercial o genérico del medicamento.
  - **Dominio:** cadena de texto que puede contener letras, números y símbolos.
  - **Ejemplos:** `Paracetamol 500mg`, `Ibuprofeno`.

- **Tipo:** clasificación del medicamento según su naturaleza o modo de uso.
  - **Dominio:** valores predefinidos como `Jarabe`, `Comprimido`, `Pomada`.
  - **Ejemplos:** `Cápsulas`, `Inyectable`.

- **Precio:** valor monetario del medicamento.
  - **Dominio:** número decimal positivo, expresado en euros.
  - **Ejemplos:** `3.50`, `12.99`.

- **Unidades Stock:** cantidad de unidades disponibles del medicamento en el inventario.
  - **Dominio:** número entero no negativo.
  - **Ejemplos:** `120`, `0`.

- **Unidades Vendidas:** cantidad total de unidades vendidas del medicamento.
  - **Dominio:** número entero no negativo.
  - **Ejemplos:** `45`, `0`.

- **Accesibilidad:** indica si el medicamento requiere receta médica o es de libre dispensación.
  - **Dominio:** únicamente dos posibles valores: `Receta médica`, `Venta libre`.

### Familia de Medicamentos

- **Código Familia:** identificador único para cada familia de medicamentos.
  - **Dominio:** cadena alfanumérica de longitud fija o variable, sin repeticiones.
  - **Ejemplos:** `FAM01`, `ANALG`.

- **Nombre Familia:** nombre común de la familia de medicamentos.
  - **Dominio:** cadena de texto de longitud variable.
  - **Ejemplos:** `Analgésicos`, `Antibióticos`.

### Tipo Enfermedad

- **Código Tipo Enfermedad:** identificador único para cada tipo de enfermedad.
  - **Dominio:** cadena alfanumérica de longitud fija o variable, sin repeticiones.
  - **Ejemplos:** `TE001`, `TE002`.

- **Nombre Tipo Enfermedad:** nombre descriptivo de la categoría de enfermedad.
  - **Dominio:** cadena de texto de longitud variable.
  - **Ejemplos:** `Infecciones bacterianas`, `Hipertensión`.

### Laboratorio

- **Código Laboratorio:** identificador único para cada laboratorio.
  - **Dominio:** cadena alfanumérica de longitud fija o variable, sin repeticiones.
  - **Ejemplos:** `LAB01`, `PFZ`.

- **Nombre Laboratorio:** nombre oficial del laboratorio.
  - **Dominio:** cadena de texto de longitud variable.
  - **Ejemplos:** `Pfizer`, `Novartis`.

- **Teléfono:** número de contacto del laboratorio.
  - **Dominio:** cadena numérica de longitud fija, aunque puede incluir prefijo internacional.
  - **Ejemplos:** `922123456`, `+34 922123456`.

- **Fax:** número de fax del laboratorio.
  - **Dominio:** cadena numérica, con un formato similar al teléfono.
  - **Ejemplos:** `922654321`.

- **Dirección Postal:** conjunto de atributos que forman la dirección del laboratorio: calle, número de vivienda, ciudad, provincia, código postal, país.
  - **Dominio:** cadenas de texto y números según cada campo: calle (cadena de texto), número de vivienda (entero no negativo), ciudad (cadena de texto), provincia (cadena de texto), código postal (cadena numérica de tamaño fijo), país (cadena de texto).
  - **Ejemplos:** `Calle Mayor 10, Santa Cruz, Tenerife, 38001, España`.

- **Nombre Persona Contacto:** nombre completo de la persona responsable en el laboratorio.
  - **Dominio:** cadena de texto de longitud variable.
  - **Ejemplos:** `Juan Pérez Torres`.

### Cliente

- **DNI:** documento nacional de identidad del cliente.
  - **Dominio:** cadena alfanumérica de formato nacional.
  - **Ejemplos:** `12345678A`, `73191185F`.

### Cliente con Crédito

- **Nombre:** nombre de pila del cliente.
  - **Dominio:** cadena de texto de longitud variable.
  - **Ejemplos:** `Ana`, `Pablo`.

- **Apellidos:** apellidos del cliente.
  - **Dominio:** cadena de texto de longitud variable.
  - **Ejemplos:** `García Pérez`, `Torres Fuentes`.

- **Datos Bancarios:**
  - **IBAN:** código internacional de la cuenta bancaria del cliente.
    - **Dominio:** cadena alfanumérica de formato internacional.
    - **Ejemplos:** `ES7620770024003102575766`.

  - **BIC/SWIFT:** código internacional de la entidad bancaria del cliente para identificar bancos en transferencias internacionales.
    - **Dominio:** cadena alfanumérica de formato internacional.
    - **Ejemplos:** `BBVAESMMXXX`.

  - **Entidad Bancaria**: nombre del banco del cliente.
    - **Dominio:** cadena de texto de longitud variable.
    - **Ejemplos:** `Banco Santander`, `BBVA`.

- **Fecha de pago:** fecha en la que se realiza el pago de todas las compras del cliente durante el mes.
  - **Dominio:** fecha válida en formato `YYYY-MM-DD`.
  - **Ejemplos:** `2025-09-30`, `2020-01-25`.

### Compra

- **Unidades:** cantidad de unidades del medicamento adquiridas en la compra.
  - **Dominio:** número entero positivo.
  - **Ejemplos:** `2`, `10`.

- **Fecha:** fecha en la que se realiza la compra.
  - **Dominio:** fecha válida en formato `YYYY-MM-DD`.
  - **Ejemplos:** `2023-02-12`, `2004-02-01`.

## Descripción de las relaciones y cardinalidad

### Jerarquía de Medicamentos

La entidad **Medicamento** se divide en dos subtipos:

- **Medicamento Fabricado**: medicamento producido directamente por la farmacia.
- **Medicamento Comprado**: medicamento comprado a laboratorios externos.

Ambos subtipos heredan los atributos generales de **Medicamento**, pero pueden diferenciarse en el origen de su procedencia.

### Jerarquía de Clientes

La entidad **Cliente** se especializa en dos subtipos:

- **Cliente Común**: realiza el pago de sus compras al instante, no dispone de datos bancarios ni fecha de pago.
- **Cliente con Crédito**: realiza el pago de sus compras a final de mes y dispone de atributos adicionales: datos bancarios (IBAN, BIC/SWIFT, entidad bancaria) y fecha de pago.

Esta jerarquía permite gestionar de forma diferenciada las condiciones de pago y la información financiera de los clientes.

### Medicamento Comprado - Laboratorio

La relación **Fabrica** relaciona un medicamento adquirido y el laboratorio al que se compra dicho producto. Un laboratorio puede fabricar varios medicamentos (como mínimo tiene que aportar uno para ser registrado), pero cada medicamento es fabricado por un único laboratorio. Cardinalidad `1:N`.

### Medicamento - Familia de Medicamentos

La relación **Pertenece a** relaciona un medicamento con la familia de medicamentos a la que pertenece. En este caso, un medicamento puede pertenecer a varias familias (mínimo tiene que pertenecer a una), y una familia puede agrupar a varios medicamentos (mínimo debe contener uno, pues de lo contrario no tendría sentido la familia). Cardinalidad `N:M`.

### Medicamento - Cliente

La relación **Compra** relaciona un cliente con el medicamento que adquiere mediante una compra. Un cliente puede comprar varios medicamentos (mínimo un medicamento ha de haber adquirido para tener el registro), y un medicamento puede ser comprado por varios clientes (mínimo ha de ser comprado por un cliente para que esta relación tenga sentido). Cardinalidad `N:M`.

### Familia de Medicamentos - Tipo Enfermedad

La relación **Se aplica** relaciona una familia de medicamentos con el tipo de enfermedad sobre la que se aplica. Una familia de medicamentos se puede usar para varios tipos de enfermedad y un tipo de enfermedad puede ser combatida por varias familias de medicamentos. Cardinalidad `N:M`.