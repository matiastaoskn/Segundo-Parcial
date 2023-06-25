# 2º Parcial-SPD "Alarma de Icendio"


Matias Skenen


![image](https://github.com/matiastaoskn/Segundo-Parcial/assets/93952537/8ac145a7-4baf-4a82-809b-dc748cb3f3db)


PROYECTO : [https://www.tinkercad.com/things/gT5FDCP5QfC-parcial-matias-skenen-spd/editel?sharecode=pw4KZWE3-n-MtK_c9UoVyWMinppxntL9BY0DAX19MYs](https://www.tinkercad.com/things/0VkikNlx48i-this-elonk-musk/editel?sharecode=NT5Waf9X8Ro0fuNkEs6rGUDPugIG1gWdchFpTOKeqSE)




GDB: [https://onlinegdb.com/JaE_Q7I0b](https://onlinegdb.com/td8VI3gWA)
## Componentes utilizados

Arduino UNO
Sensor de temperatura
Control remoto IR (Infrarrojo)
Display LCD (16x2 caracteres)
Servo motor
Cables y resistencias según sea necesario
Protoboard para realizar las conexiones
Dos leds.

## Configuración de pines

El código utiliza los siguientes pines para conectar los componentes:

```
#include <LiquidCrystal.h>
#include <IRremote.h> 
#include <Servo.h>

LiquidCrystal led(2,3,4,5,6,7);
Servo servomotor;
decode_results results;


#define DECODE_NEC
#define pin_Receptor 11

int motor = 9;
int lecturaIR; 
int codigo = 0;
int led1 = 13;
int led2 = 12;

int TMP = 0;
float temperatura = 0;

int programa;
int encendido = false;
int controlActivado = 0;
```


## Bucle principal

En el bucle principal `loop`, se llama a la función `controladorMontacargas()` 


```cpp
void loop()
{
  controlRemotoIr();
  if (encendido == true)
  {
    //ECENDIDO
    sensorTemperatura();
    displayLCD();
    ServoMotor();
    Serial.println(controlActivado);
    
  } 
  else
  {
    //APAGADO
    
  }
```



