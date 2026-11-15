# Datos del proyecto

El notebook utiliza este CSV público:
https://raw.githubusercontent.com/JuanTF/BPA---Datasets/refs/heads/main/hotel_bookings.csv

La copia utilizada tiene columnas como `Hotel`, `IsCanceled`, `LeadTime` y `ArrivalDateYear`. No debe sustituirse por cualquier dataset llamado hotel_reservations: el esquema tiene que coincidir.

El archivo no se incluye en este paquete. La URL apunta a una rama que puede cambiar; para reproducibilidad conviene registrar una revisión fija y el hash del CSV. Antes de redistribuirlo, documenta la fuente original, las modificaciones y la licencia aplicable.

Los archivos intermedios del notebook se crean en `artifacts/` al ejecutar las etapas anteriores. El PBIX conserva su propio origen de datos, que debe revisarse por separado en Power BI Desktop.
