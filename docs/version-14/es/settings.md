# Configuración de ejecución de cheques

Una entrada de `Configuración de ejecución de cheques` determina el comportamiento en una ejecución de cheques para una combinación específica de cuenta bancaria/cuenta por pagar. Deberá confirmar configuraciones separadas para cada combinación de cuenta bancaria/cuenta por pagar que planee usar en una ejecución de cheques.

![Captura de pantalla de la vista de lista Configuración de ejecución de cheques con dos entradas: una para la combinación de banco local y nómina por pagar y la otra para la combinación de banco local y cuentas por pagar.](./assets/SettingsList.png)

Si el sistema no encuentra configuraciones para la combinación de cuenta que está usando en una ejecución de cheques iniciada, lo llevará automáticamente a la página de configuraciones para confirmar las opciones. Alternativamente, puede acceder a la lista de configuraciones directamente buscando "Lista de configuraciones de ejecución de cheques" en AwesomeBar y haciendo clic en el botón `Agregar configuraciones de ejecución de cheques`.

![Captura de pantalla que muestra la parte superior de las configuraciones predeterminadas para una combinación de cuenta bancaria y cuenta por pagar. A continuación, se incluye una descripción de cada configuración y su valor predeterminado.](./assets/Settings_Main.png)

- **Incluir facturas de compra:**
- Seleccionado de forma predeterminada
- Indica si las facturas de compra se incluyen o no en una ejecución de cheque. Consulte a continuación para obtener más información y algunas consideraciones sobre las facturas de compra con un cronograma de pago definido
- **Incluir asientos de diario:**
- Seleccionado de forma predeterminada
- Indica si las entradas de diario se incluyen o no en una ejecución de cheque. Por ejemplo, los datos de demostración tienen una entrada de diario para los impuestos de nómina adeudados a la autoridad fiscal local; esto solo se mostrará en una ejecución de cheque si se selecciona esta configuración
- **Incluir reclamos de gastos:**
- Seleccionado de manera predeterminada
- Indica si los reclamos de gastos se incluyen o no en una ejecución de cheque
- Consulte la [página de configuración](./configuration.md) para obtener instrucciones sobre cómo configurar un modo de pago, banco y cuenta bancaria predeterminados para un `Empleado`
- **Elementos vencidos de verificación previa:**
- No seleccionado de manera predeterminada
- Indica si la casilla de verificación "Pagar" está preseleccionada para cualquier elemento cuya fecha de vencimiento sea anterior a la fecha de contabilización de la ejecución de cheque
- **Permitir cancelación:**
- No seleccionado de manera predeterminada
- Indica si un usuario puede cancelar o no una ejecución de cheque. Si se selecciona y un usuario cancela una ejecución de cheque, el sistema eliminará la referencia al nombre del documento de ejecución de cheque en todas las entradas de pago que se realizaron a través de la ejecución, pero no cancelará las entradas de pago en sí.
- **Cancelación en cascada:**
- No seleccionado de forma predeterminada (¡no se recomienda seleccionar esta opción!)
- Indica si el sistema cancelará o no todas las entradas de pago asociadas con una ejecución de cheque si se cancela la ejecución de cheque
- **Número de facturas por comprobante:**
- El valor predeterminado muestra 0, lo que le indica al sistema que esta configuración no se modifica y que utilizará 5 facturas por comprobante
- Esta configuración es un límite superior para la cantidad de facturas por parte que se agruparán en cada comprobante para esa parte
- La captura de pantalla a continuación muestra el resultado de una ejecución de cheque enviada donde la configuración de Número de facturas por comprobante se estableció en 2. De las cuatro facturas pagadas a Exceptional Grid, se agrupan de modo que dos se pagan con un comprobante y luego las otras dos se pagan con un comprobante diferente
- Esto también se puede configurar por proveedor en el campo "Número de facturas por comprobante de cheque". La configuración por proveedor anula el número en Configuración de ejecución de cheque
- **Dividir facturas por dirección:**
- Si está marcada, esto validará si se le paga al mismo proveedor en diferentes direcciones y dividirá las entradas de pago de manera adecuada
- **Liberar automáticamente facturas en espera:**
- De manera predeterminada, las facturas en espera no se mostrarán si su "fecha de liberación" no está dentro del período de ejecución de cheque. La casilla de verificación permite que las facturas que _están_ en espera se liberen y paguen automáticamente en la ejecución de cheque.
- **Establecer fecha de contabilización de entrada de pago:**
- De manera predeterminada, la ejecución de cheque usará la fecha de hoy para determinar la contabilización en las entradas de pago. Al cambiar esta configuración, puede retroceder o adelantar la fecha. La fecha de referencia en la entrada de pago siempre usa la fecha de contabilización de la ejecución de cheque. Cualquiera de estos campos se puede utilizar en sus formatos de impresión personalizados.

![Tabla de resultados de la ejecución de la comprobación que muestra una fila para ocho facturas pagadas (dos para AgriTheory, dos para Cooperative Ag Finance y cuatro para Exceptional Grid). Las dos primeras facturas de Exceptional Grid tienen el número de referencia de comprobación ACC-PAY-2022-00003 y el siguiente conjunto de dos facturas tiene el número de referencia de comprobación ACC-PAY-2022-00004. Se dividieron en comprobantes diferentes porque la configuración limitaba dos facturas por comprobante.](./assets/VoucherGroup.png)

La siguiente sección de configuraciones permite un modo de pago predeterminado opcional para facturas de compra, reclamos de gastos y asientos de diario. Si no hay un modo de pago especificado en la factura de compra, el reclamo de gastos o el asiento de diario en sí, y no hay un valor predeterminado establecido para la parte (consulte la [página de configuración](./configuration.md) para obtener más detalles), este campo se utiliza para completar la columna Modo de pago en la ejecución de la comprobación.

![Captura de pantalla que muestra la sección Modo de pago predeterminado en la configuración.](./assets/Settings_MOP.png)

También hay una sección para todas las configuraciones relacionadas con los pagos ACH.

![Captura de pantalla que muestra la sección Configuración de ACH. A continuación, se incluye una descripción de cada configuración y su valor predeterminado.](./assets/Settings_ACH.png)

- **Extensión de archivo ACH:**
- El valor predeterminado es "ach"
- Una ejecución de cheque genera automáticamente un archivo ACH si alguna de las opciones de Modo de pago utilizadas tenía un tipo de "Electrónico". Esta configuración es un campo de texto para indicar la extensión de archivo que utilizará el sistema cuando cree estos archivos. Es posible que su institución bancaria requiera una extensión determinada
- Consulte la [página de configuración](./configuration.md) para obtener instrucciones sobre cómo indicar que un `Modo de pago` es una transferencia bancaria electrónica
- **Código de clase de servicio ACH:**
- El valor predeterminado es 200
- Las opciones incluyen 200 (débitos y créditos combinados), 220 (solo créditos) y 225 (solo débitos). Este es un valor obligatorio para los campos del archivo ACH y debe reflejar la naturaleza de sus pagos de transferencia bancaria electrónica
- **Código de clase estándar de ACH:**
- El valor predeterminado es PPD (entrada de depósito y pago preestablecido)
- PPD es el único código de clase de entrada estándar admitido en este momento
- **Descripción de ACH:**
- El valor predeterminado está en blanco
- Campo opcional para agregar una descripción a los archivos ACH

## Consideraciones para facturas de compra con cronogramas de pago

Una característica de Check Run para facturas de compra con un cronograma de pago definido es que desglosará y mostrará transacciones separadas para cada término de pago pendiente del cronograma de pago por fecha de vencimiento en lugar del monto total de la factura.

El siguiente ejemplo supone una factura de compra por un alquiler de equipo de $30,000 por 18 meses que se paga mediante un cronograma de pago en 18 cuotas mensuales iguales.

![Captura de pantalla de las transacciones de Check Run para Tireless Equipment Rental, Inc desde principios de año hasta mayo. Muestra transacciones separadas para cada mes por $1,666.67 cada una, lo que refleja los pagos mensuales vencidos en el Programa de Pagos.](./assets/PaymentScheduleTransactions.png)

Check Run aprovecha el mecanismo ERPNext integrado que actualiza automáticamente el Programa de Pagos de una factura cuando una Entrada de Pago se vincula a un Plazo de Pago en el programa. Hay algunas suposiciones y consideraciones de ERPNext que se deben tener en cuenta al configurar sus Programas de Pagos o realizar Entradas de Pago en función de ellos para garantizar que este mecanismo funcione correctamente, tanto dentro como fuera de una Check Run:

1. Para un Programa de Pagos de varias filas, cada fila debe vincularse a un Plazo de Pago único. Esto actúa como la "clave" para identificar correctamente la cuota en el Programa de Pagos que se vincula a la Entrada de Pago y actualizar el programa en consecuencia.

![Captura de pantalla de un ejemplo de Programa de Pagos definido en una factura de compra. La columna Plazo de pago de la tabla se vincula a documentos únicos, como "Cuota de alquiler 1", "Cuota de alquiler 2", etc. para las distintas filas.](./assets/InvoicePaymentScheduleExample.png)

2. Si está creando una Entrada de pago fuera de una Ejecución de cheque que corresponde a una parte de una factura (para cumplir con un Plazo de pago), existe una validación para verificar y vincular el Plazo de pago pendiente más reciente. Si el campo Plazo de pago en la tabla Referencias de pago se deja en blanco, intenta completar el campo y advierte al usuario que lo revise. Si la Entrada de pago cubre varios Plazos de pago, debe haber una fila para cada parte del pago con un vínculo a su Plazo de pago respectivo.

![Captura de pantalla del cuadro de diálogo del formulario cuando se edita una fila en la tabla Referencias de pago. El campo Plazo de pago muestra un valor de "Cuota de alquiler 3" para vincular el monto asignado del pago al plazo correspondiente en el Programa de pago de la factura.](./assets/PaymentEntryPaymentTerm.png)

