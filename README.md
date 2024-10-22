Este código te convierte los valores que ofrece el transudctor y establece un límite superior e inferior creando así una escala de medida de humedad expresada en porcentaje.

Deberás hallar una media de los valores recibidos en el monitor serie en seco, luego deberás hacerlo en mojado totalmente.

Los valores medios serán sustituidos en las siguientes constantes:

const int DRY_MEDIA_VALUE = "tu valor medio en seco";

const int WET_MEDIAVALUE = "tu valor medio en mojado";

El valor medio será más preciso cuantos más valores instantaneos incluyas en la media. (Yo incluí 100 valores).
