#include <Arduino.h>
#include <LiquidCrystal_I2C.h>


//Constantes

const int DRY_MEDIA_VALUE = 628;
const int WET_MEDIAVALUE = 233;
const int SENSOR_HUM_PIN = 35;

const int I2C_SDA_PIN= 21;
const int I2C_SCL_PIN = 22;

const int NUM_COL_LCD = 16;
const int NUM_FIL_LCD = 2;

//Liquid cristal configuracion

LiquidCrystal_I2C lcd (0x27, NUM_COL_LCD, NUM_FIL_LCD);

//Subprogramas

void setup (){

  Serial.begin(115200);
  analogReadResolution(10); //Resolución de la toma de datos

  //Inicializar I2C

  lcd.init(I2C_SDA_PIN, I2C_SCL_PIN);
  lcd.backlight();

}

int porcentaje (int dryMediaValue, int wetMediaValue, int instantValue){

  int result;

  /*
  Como dryMediaValue y wetMediaValue que son los límites son una media,
  el valor instantáneo en seco y en mojado podría ser mayor a estos límites.

  Para solucionarlo se hace uso del if.
  */

  if (instantValue >= dryMediaValue) {

    result = 0;

  } else if (instantValue <= wetMediaValue) {

    result = 100;

  } else {

    result = float(dryMediaValue-instantValue) / float(dryMediaValue-wetMediaValue) * 100;

  }

  return result;

}

//Principal

void loop (){

  int instantValue = analogRead(SENSOR_HUM_PIN); // Toma los valores del pin 35
  int porcentajeValue = porcentaje(DRY_MEDIA_VALUE, WET_MEDIAVALUE,instantValue);

  Serial.print("Valor calculado: "); Serial.print(porcentajeValue); Serial.println('%');

  lcd.setCursor(3,0); lcd.print("Humedad:");
  lcd.setCursor(3,1); lcd.print(porcentajeValue); lcd.print('%');

  delay (500);

}
