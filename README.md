> NOTA: Para todos los ejercicios puede utilizar el lenguaje de programación que desee.
---
# Ejercicio práctico #1
> Se tiene una interfaz de cliente configurada en un equipo marca CISCO, la configuración se muestra en el archivo config.txt
```
Building configuration...

Current configuration : 253 bytes
!
interface GigabitEthernet0/1.1969
 description vazseguroseditorresnorte-gye_2
 encapsulation dot1Q 1969
 ip vrf forwarding linkotel3_95
 ip address 10.211.249.1 255.255.255.0
 no ip redirects
 no ip unreachables
 no ip proxy-arp
 arp timeout 300
end
```
> Se desea cambiar el equipo del cliente por un equipo marca HUAWEI, con la observación que los comandos de configuración en HUAWEI no son los mismos que los de CISCO.
>
> Para esto, debemos realizar los siguientes pasos.
> - Modelar la configuracion del puerto como un objeto.
> - Poblar el objeto con las propiedades de la interfaz.
> - Crear un nuevo archivo de configuracion usando los valores almacenados en el objeto.
>

## Tarea #1
Crear el objeto `Puerto` que tenga las siguientes propiedades: 
- Descripcion
- Vlan
- VRF
- IP Address
- Mascara de red

## Tarea #2
Parsear el archivo config.txt linea a linea e ir almacenando las propiedades del objeto `Puerto`. En negritas se identifica las propiedades a almacenar.
<pre>
interface GigabitEthernet0/1.1969
 description <b>vazseguroseditorresnorte-gye_2</b>      <- (Descripcion) 
 encapsulation dot1Q <b>1969</b>                        <- (Vlan)
 ip vrf forwarding <b>linkotel3_95</b>                  <- (VRF)
 ip address <b>10.211.249.1</b> <b>255.255.255.0</b>           <- (IPAddress & Mascara)
 no ip redirects
 no ip unreachables
 no ip proxy-arp
 arp timeout 300
</pre>

## Tarea #3
Crear un array armando la nueva configuración para el equipo HUAWEI, segun la plantilla de abajo. Reemplazar los tags por las propiedades del objeto `Puerto`
```
interface Vlanif<vlan>
 mtu 1546
 description <descripcion>
 ip binding vpn-instance <vrf>
 ip address <IP Address> <Mascara>
```
> Ejemplo de configuracion correcta
```
interface Vlanif2020
 mtu 1546
 description pruebas_networking
 ip binding vpn-instance networking
 ip address 192.168.1.1 255.255.255.0
```

## Tarea #4
Mandar el arreglo a un archivo de nombre config_huawei.txt

***

# Ejercicio práctico #2
> En el archivo data.csv encontrará la información del tráfico consumido por el cliente a partir de la fecha `2019-04`, a continuación se describe cada una de sus columnas:
- date (Fecha en formato YYYY-MM)
- pc (Tráfico Percentil 95, en Megabits/segundo)
- max (Tráfico Máximo, en Megabits/segundo)

## Tarea
***En un solo gráfico*** mostrar la evolución de ambos tráficos (pc & max) a lo largo del tiempo. 

Puede escoger el tipo de gráfico que mejor se ajuste para mostrar la información (Area, Linea, Barra).

Puede escoger si mostrar el gráfico desde la aplicación o generar un archivo .png, .jpeg, etc.
