# arquitectura-web-tp
TP Aplicación de control de finanza personal
Materia: Arquitectura web
Profesor: Diego Marafetti
Alumna: Maria Alicia Patiño Leguizamon
Legajo: 0113728

Una aplicación web de gastos e ingresos fijos y eventuales. Pueden ser compartidos o personales. 
Podes ingresar gastos e ingresos:
Fijos, donde se replicaran todos los meses automáticamente.
Eventuales, puede ser al mes en curso, o a futuro. Por ejemplo, en noviembre bono por desempeño y lo puede cargar meses antes, o pago de matrícula de la facultad.

Cuando agregue un gasto ingresa el medio de pago. Si es tarjeta de credito, puede poner la cantidad de cuotas y que se refleje mes a mes automaticamente. 
Una sección con préstamos dados o recibidos de familiares o amigos donde cargar el monto, la fecha de devolución comprometida, las devoluciones parciales, con fecha y monto, a quien o quien me presto. 
Ahorros, en plazo fijo, bonos, saldo en cuenta, en efectivo. 
Una visualización de patrimonio neto.

Métodos:

POST \personas\{DNI}\gastos

Descripción: Ingresa gastos de la persona 

Request:

{
"id": 1,
"descripcion": "Kiosco";
"medio_pago": "EFECTIVO", 
"cantidad_cuotas": 1,
"fecha": 20200718,
"compartido": [true/false],
"compartido_con": 35111222, (DNI de la persona con la q comparte)
"estado": "PENDIENTE_PAGO" ENUM= PENDIENTE_PAGO, PAGADO
}

DELETE \personas\{DNI}\gastos\{id}

Descripción: Elimina un gasto

PATCH \personas\{DNI}\gastos\{id}

Descripción: Actualiza el estado de un gasto

Request:
{
"estado" : "PAGADO"  ENUM= PENDIENTE_PAGO, PAGADO
}

GET \personas\{DNI}\gastos?mes_año&compartido=[true/false]&orden[asc/desc]&sortBy=fecha

Descripción: Devuelve la lista de gastos de la persona

[
{
"id": 1,
"descripcion": "Kiosco";
"medio_pago": "EFECTIVO",
"cantidad_cuotas": 1,
"fecha": 20200718,
"compartido": true,
"compartido_con": 35111222, (DNI de la persona con la q comparte)
"estado" : "PAGADO"  ENUM= PENDIENTE_PAGO, PAGADO
}
]





