# Ejercicios Tema 1

### Ejercicio 1
#### Consultar en el catálogo de alguna tienda de informática el precio de un ordenador tipo servidor y calcular su coste de amortización a cuatro y siete años. Consultar este [artículo](http://infoautonomos.eleconomista.es/consultas-a-la-comunidad/988/) en Infoautónomos sobre el tema.

La tienda que voy a consultar es una conocida por casi todos, PcComponentes, en ella con una [simple consulta](https://www.pccomponentes.com/buscar/?query=servidor#p0-f1517) de servidor obtenemos distintos tipos de ordenadores de tipo servidor que cumplen con lo que necesitamos.

En mi caso voy a realizar los calculos sobre [HP ProLiant BL460c Gen9 E5-2620v3](https://www.pccomponentes.com/hp-proliant-bl460c-gen9-e5-2620v3) cuyo precio es de 2157€.

#### Amortización a cuatro años.
Suponemos que el ordenador se compra a principios de año, pues como se dice en el articulo, si el ordenador se compra después de mitad de año solo podremos amortizar la mitad ese año.

Tenemos que quitar el IVA, que es el 21% del precio que pagamos del artículo. Tendríamos entonces un precio sin IVA de:
> 2157/1,21 = 1782,64 €.

Ahora al ser la amortización a cuatro años tenemos que dividirlo por 4:
> 1782,64/4 = 445,66 €/año

Por lo cual tendremos una amortización de 445,66€ por año.

#### Amortización a siete años.
Teniendo el mismo supuesto que en la amortización de cuatro años, tenemos el mismo precio sin IVA, lo único que cambia es que hay que dividirlo por siete.

Ahora al ser la amortización a siete años tenemos que dividirlo por 7:
> 1782,64/7 = 254,66 €/año

Por lo cual tendremos una amortización de 254,66€ por año.


### Ejercicio 2
#### Usando las tablas de precios de servicios de alojamiento en Internet y de proveedores de servicios en la nube, Comparar el coste durante un año de un ordenador con un procesador estándar (escogerlo de forma que sea el mismo tipo de procesador en los dos vendedores) y con el resto de las características similares (tamaño de disco duro equivalente a transferencia de disco duro) en el caso de que la infraestructura comprada se usa sólo el 1% o el 10% del tiempo.

En [Strato](https://www.strato.es/vps-linux/) encontramos distintos servicios de alojamiento en Internet para poder elegir el que más se adapte a lo que necesitamos. Escojo Linux L3 que tiene las siguientes caracteristicas:
~~~~~~~
8 CPU vCores
Hasta 16 GB RAM
600 GB SSD/HDD
~~~~~~~
Cuyo precio es de 24,90 €/mes.

En [Axarnet](https://www.axarnet.es/servidores-cloud/) encontramos distintos servidores cloud para poder elegir el que más se adapte a nuestras necesidades. Escojo Cloud L que tiene las siguientes caracteristicas:
~~~~~~~
8 GB RAM
2 vCPU
250 GB Disco
~~~~~~~
Cuyo precio es de 49,95 €/mes.

#### Para un uso anual del 1%

Redondeo hacia arriba.

Strato  -> 24,90€/mes * 1% = 0,25€/mes
> 0,25€/mes * 12 meses = 3€ al año

Axarnet -> 49,95 * 1% = 0,50€/mes
> 0,50€/mes * 12 meses = 6€ al año

#### Para un uso anual del 10%

Redondeo hacia arriba.

Strato  -> 24,90€/mes * 10% = 2,5€/mes
> 2,5€/mes * 12 meses = 30€ al año

Axarnet -> 49,95 * 10% = 5€/mes
> 5€/mes * 12 meses = 60€ al año

Como se puede ver el servidor en la nube es el doble de caro.

### Ejercicio 3
#### ¿Qué tipo de virtualización usarías en cada caso? Comentar en el foro

Mirar respuesta en el [issue](https://github.com/JJ/IV16-17/issues/1) correspondiente

#### Crear un programa simple en cualquier lenguaje interpretado para Linux, empaquetarlo con CDE y probarlo en diferentes distribuciones.

Al ser un programa simple, el más simple que a cualquiera se le ocurriría es el típico "Hola mundo!!!", y básicamente ese es el programa:
> print "Hola mundo!!!"

Ahora, lo siguiente será instalar CDE:
> sudo apt-get install cde

Para empaquetar el programa y poder ejecutarlo, se utiliza el comando:
>cde python ej3.py

### Ejercicio 4
#### Comprobar si el procesador o procesadores instalados tienen estos flags. ¿Qué modelo de procesador es? ¿Qué aparece como salida de esa orden?

Comprobamos que flags tiene el procesador.
~~~~~~~~~
$ egrep '^flags.*(vmx|svm)' /proc/cpuinfo
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer xsave avx f16c rdrand lahf_lm epb tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms xsaveopt dtherm ida arat pln pts
~~~~~~~~~
Se puede ver que efectivamente tengo el flag vmx activado, por lo cual es posible la virtualización.

Ahora usando *cat /proc/cpuinfo* veo que modelo de procesador tengo:
~~~~~
$ cat /proc/cpuinfo
  processor	: 0
  vendor_id	: GenuineIntel
  cpu family	: 6
  model		: 58
  model name	: Intel(R) Core(TM) i5-3337U CPU @ 1.80GHz
  stepping	: 9
  microcode	: 0x1c
  cpu MHz		: 799.945
  cache size	: 3072 KB
  physical id	: 0
  siblings	: 4
  core id		: 0
  cpu cores	: 2
  apicid		: 0
  initial apicid	: 0
  fpu		: yes
  fpu_exception	: yes
  cpuid level	: 13
  wp		: yes
  flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer xsave avx f16c rdrand lahf_lm epb tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms xsaveopt dtherm ida arat pln pts
  bugs		:
  bogomips	: 3591.69
  clflush size	: 64
  cache_alignment	: 64
  address sizes	: 36 bits physical, 48 bits virtual
  power management:
~~~~~
El modelo de procesador es Intel(R) Core(TM) i5-3337U CPU @ 1.80GHz

### Ejercicio 5
#### Comprobar si el núcleo instalado en tu ordenador contiene este módulo del kernel usando la orden kvm-ok.

Para poder usar kvm-ok primero se debe de instalar el paquete cpu-checker, para ello al usar Linux Mint será necesario hacer:
> sudo apt-get install cpu-checker

Una vez instalado dicho paquete podremos obtener la información que necesitamos, en mi caso la consola devuelve:
~~~~~~
$ kvm-ok
INFO: /dev/kvm exists
KVM acceleration can be used
~~~~~~
Por lo cual puedo usar la aceleración por hardware del procesador.

#### Instalar un hipervisor para gestionar máquinas virtuales, que más adelante se podrá usar en pruebas y ejercicios.

En mi caso tengo instalados tanto VirtualBox como VMWare desde hace tiempo. Si se desea instalar VirtualBox bastará con:
> sudo apt-get install virtualbox-qt

Para la instalación de VMWare, será necesario ir a su página web y seguir los pasos que allí se indican.
