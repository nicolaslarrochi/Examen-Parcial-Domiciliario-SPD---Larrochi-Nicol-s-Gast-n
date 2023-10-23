# **Examen Parcial Domiciliario:** Sistemas de procesamiento de datos

![Tinkercad](./Img/ArduinoTinkercad.jpg)
## *Division E*
## **Profesores**
- Dario Cuda
- Esteban Quiroz
## **Alumno:**
- Nicolás Gastón Larrochi

## **Parcial domiciliario - Sistemas de procesamiento de datos** 
Parte 4: Modificación según el Último Número de Documento**

![Tinkercad](./Img/Examen%20Parcial%20Domiciliario_1-E%20%20Larrochi%20Nicol%C3%A1s%20Gast%C3%B3n%20.png)

## Descripción

En este proyecto, se modificó gran parte del código, para que se mantenga las opciones que da el proyecto.

El interruptor deslizante tiene la función de encender y apagar el sistema, solo mostrando el contador.

Si no se enciende el switch, el sistema permanece apagado.

Al encender el Switch, enciende el contador, y por cada vez que se pulsa un botón, mostrará por consola los valores del sensor de fuerza (Si se presiona restar numeros) o de los de la fotoresistencia (Si se presiona sumar numeros).

Se mostrarán estos valores por cada vez que se presione el boton.

Y según los valores que tome el sensor de fuerza y la fotoresistencia, movilizará o mantendrá en reposo el motor de aficionado.


## Fragmento del código principal.

Este fragmento de código muestra como es que interactuan todos los dispositivos entre si, en este caso, si se pulsa del switch y si se presiona suma

``` c+
  if (digitalRead(SWITCH) == HIGH) // Si se presiona el Switch, enciende el sistema
  {                                // enciende el contador
                                   
     if (pressed == SUMA) // Si se presiona suma,
     {                    // sumará 1 al contador
                          // Por cada vez, la fotoresistencia se activa y muestra valores
                          // y dirige si el motor enciende o no segun sus valores      
         
       countDigit++;
       if (countDigit > 99)
       {
         countDigit = 0;  // Si ese contador está en 99 y suma
       }                  // retornará 0  
       
        // Esto muestra los valores de la fotoresistencia.
        // El motor gira según los valores de la fotoresistencia.
        lecturaFotoresistencia = analogRead(FOTORESISTENCIA); // Lectura
        Serial.println(lecturaFotoresistencia); // Muestra
        delay(10); 
                                                    // Valor de lectura de Fotoresistencia   
        analogWrite(POSITIVO, lecturaFotoresistencia); // de 6 a 118 = 0 | Motor en reposo
                                                    // de 158 a 679 = +30  | Motor en movimiento 
        digitalWrite(NEGATIVO, LOW);  // Gira en positivo

```

## Link al proyecto

- [Tinkercad - Parte 1](https://www.tinkercad.com/things/cHaGmhaJGJR)
