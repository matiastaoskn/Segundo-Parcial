# 2º Parcial-SPD "Alarma de Icendio"


Matias Skenen




PROYECTO : [https://www.tinkercad.com/things/gT5FDCP5QfC-parcial-matias-skenen-spd/editel?sharecode=pw4KZWE3-n-MtK_c9UoVyWMinppxntL9BY0DAX19MYs](https://www.tinkercad.com/things/0VkikNlx48i-this-elonk-musk/editel?sharecode=NT5Waf9X8Ro0fuNkEs6rGUDPugIG1gWdchFpTOKeqSE)




GDB: https://onlinegdb.com/JaE_Q7I0b
## Componentes utilizados

- Arduino Uno
- Display de 7 segmentos
- Resistencias
- Botones
- LED verde y LED rojo

## Configuración de pines

El código utiliza los siguientes pines para conectar los componentes:

```
#define LED_ROJO 13
#define LED_VERDE 12

#define LED_A 7
#define LED_B 6
#define LED_C 5
#define LED_D 4
#define LED_E 3
#define LED_F 2
#define LED_G A4

#define botonSubir 11
#define botonBajar 10
#define botonDetener 9

int nivel = 0;
int piso;
int botonSubida;
int botonBajada;
int botonDetenido;

int montaCargaSUBIENDO = false;
int montaCargaBAJANDO = false;

int botonEmergencia = false;
int acumuladorEmergencia = 0;
```


## Bucle principal

En el bucle principal `loop`, se llama a la función `controladorMontacargas()` 

## Función `controladorMontacargas()`
```cpp
if(nivel == 0)
  {
    montacarga();
  }
  
  //Boton de emergencia, deterner.
  if(botonDetenido == 0)
  {
    acumuladorEmergencia += 1;
    delay(1000);
    Serial.println("Emergencia Activado");
  }
  
	// Comienzo de programa
  if(acumuladorEmergencia % 2 == 0)
  {
    if(botonSubida == 0 || botonBajada == 0)
    {
      if(botonBajada == 0)
      {
        nivel -= 1;
        prenderLeds(0, 0, 0, 0, 0, 0, 0, 3000);
        montacarga();
        mostrarPiso();
      }
      else
      {
        if(nivel >= 9)
        {
          piso = 9;
          prenderLeds(1, 1, 1, 1, 0, 1, 1, 3000);
          mostrarPiso();
        }
        else
        {
          prenderLuces(LED_VERDE);
          apagarLuces(LED_ROJO);
          nivel += 1;
          prenderLeds(0, 0, 0, 0, 0, 0, 0, 3000);
          montacarga();
          mostrarPiso();
        }

      }
    }
  }
```


![DIAGRAMA](https://github.com/matiastaoskn/PARCIAL-SPD1/assets/93952537/955de3e1-3e17-4213-8f5c-83232bc0b114)

