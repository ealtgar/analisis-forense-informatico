# 1. Fuentes de evidencia

- **En el puesto de Marta:**
	- Portátil Dell
	- Disco duro externo de 2 TB
	- IPhone de empresa
- **Otras ubicaciones de la oficina:**
	- Pendrive prestado, actualmente en el cajón del puesto de Javier.
	- Historial de trabajos (logs y caché) de la impresora multifunción.
	- PC compartido (posibles rastros de conexión de USBs o sesiones temporales).
	- Servidor local de ficheros y el NAS con las últimas 14 copias de seguridad.
- **En la nube / terceros:**
	- Logs del cortafuegos perimetral (tráfico de red y conexiones VPN).
	- OneDrive corporativo y buzón de correo de Marta.
	- Portal de Microsoft / Bahía Sistemas (logs de acceso de Entra ID/Intune y claves de BitLocker).
	- Grabaciones de la cámara de seguridad del pasillo (conserjería).

# 2. La prioridad (Orden de recolección por volatilidad)

El orden de actuación no se basa en lo que tenemos más cerca, sino en lo que desaparecerá primero:

1. **Prioridad CRÍTICA (Desaparición inminente): Logs del cortafuegos y Grabaciones.** El firewall guarda logs "*sobre una semana*". El jueves 14 (día del comportamiento anómalo) fue hace 6 días (Elena nos llamo el día 20). Estamos a horas de que esos logs se sobrescriban. Las cámaras de conserjería también suelen tener bucles de grabación muy cortos.
2. **Prioridad 1 (Volatilidad de Sistema): Memoria RAM del Dell.** El equipo está encendido. La RAM contiene las claves de descifrado de BitLocker en claro, archivos temporales del render si los abrió, y el registro de conexiones activas. Si el equipo entra en suspensión o se apaga, esto se esfuma.
3. **Prioridad 2 (Volatilidad en la Nube/Sincronización): OneDrive y iPhone corporativo.** Si Marta o su amiga Lucía tienen acceso remoto a la cuenta corporativa, podrían borrar los archivos exfiltrados de OneDrive o enviar un comando de borrado remoto (Wipe) al iPhone.
4. **Prioridad 3 (Baja Volatilidad): Discos físicos y Pendrive.** El disco del portátil, el HDD de 2TB y el pendrive de Javier retienen la información sin energía. Se adquirirán los últimos, una vez asegurada la clave de BitLocker.

# 3. Las medidas inmediatas (Qué hacer AHORA MISMO)

- **A la persona sospechosa (Marta):** Apartarla de inmediato (y con educación) de su puesto de trabajo. No puede seguir trabajando ni usar el iPhone de empresa. Se le pide que no utilice su móvil personal para contactar con nadie de la oficina ni de fuera hasta aclarar la situación inicial.
- **A Bahía Sistemas:**
	- Que exporten y salvaguarden INMEDIATAMENTE los logs del firewall (especialmente tráfico VPN y conexiones del día 14).
	- Que revoquen el acceso de la cuenta de Marta (`mgarcia`) a Microsoft 365/OneDrive para congelar la nube y evitar borrados, y que nos exporten la clave de recuperación de BitLocker de su Dell.
- **Al Portatil y HDD externo: NO APAGAR**. Desconectar el cable de red (Ethernet) del dock o desactivar el Wi-Fi para aislarlo, pero mantenerlo conectado a la corriente para evitar que se hiberne. Insertaremos nuestro USB forense para extraer la memoria RAM en vivo.
- **Al IPhone corporativo:** Ponerlo inmediatamente en Modo Avión o meterlo en una funda Faraday para aislarlo de la red celular/Wi-Fi y evitar un borrado remoto.
- **A la Conserjería:** Enviar a alguien de inmediato con una solicitud formal de la gerencia para paralizar el borrado y exportar las grabaciones de la cámara del pasillo correspondientes a la tarde/noche del jueves 14.
- **A la Impresora:** Acceder al menú de administración (físico o web) y exportar/fotografiar el historial de trabajos antes de que alguien imprima y lo sobrescriba.
- **A la escena en sí:** Documentar el estado general de la escena mediante fotografías y un croquis detallado de la ubicación de cada equipo y sus conexiones.
- **Al Pendrive de Javier:** Recogerlo, introducirlo en una bolsa anti-ESD e iniciar su cadena de custodia.

# 4. Los límites (Qué NO tocar y por qué)

- **El móvil personal en el bolso de Marta:** **PROHIBIDO TOCAR.** Es un dispositivo de su propiedad privada. No existe autorización legal ni política de empresa (BYOD) que nos ampare para incautarlo o registrarlo sin su consentimiento expreso o una orden judicial. Hacerlo constituiría un delito de descubrimiento y revelación de secretos, invalidando la prueba. _Alternativa:_ Vigilar visualmente que no lo use para avisar a su cómplice y, si hay sospechas graves, recomendar a gerencia la denuncia policial para que un juez ordene su intervención.
- **Apagar el portátil de golpe (Pull the plug):** **NO HACERLO.** 
	- Si apagáramos el portátil sin haber realizado el volcado de la memoria y otras fuentes de datos volátiles, perderíamos toda la información que existía en ese momento en la memoria RAM. 
	- Tiene BitLocker activado. Si tiramos del cable sin haber volcado la memoria RAM o sin haber verificado que Bahía Sistemas nos ha dado la clave de recuperación correcta (cotejando el Key ID), perderemos el acceso a todos los datos del disco duro para siempre.
- **La sesión de la compañera en el PC compartido:** No husmear en el correo web abierto de la otra empleada. Se vulneraría su privacidad sin justificación. Solo se analizarán los logs del sistema operativo de esa máquina (conexión de dispositivos USB).

# 5. De dónde sale cada decisión (Trazabilidad con la checklist)

- Apartar a Marta de los equipos $\rightarrow$ **Punto 3 de la lista** *(ENFSI BPM §8.2)*
- No tocar el teléfono personal de Marta del bolso $\rightarrow$ **Puntos 2 y 12 de la lista** *(NIST SP 800-86 §3.1.1 - Fronteras legales y políticas corporativas)*.
- *Documentar el estado de general de la escena mediante fotografías y un croquis de la ubicación de los dispositivos.* $\rightarrow$ **Punto 5 de la lista** *(ENFSI BPM §8.2)*
- Inspección visual expansiva de periféricos, memorias USB, etc. $\rightarrow$ **Punto 6 de la lista** *(NIST SP 800-86 §3.1.1)*
- No apagar el portátil Dell (encendido = RAM viva) $\rightarrow$ **Punto 7 de la lista** (*RFC 3227 §2.2 / ENFSI BPM §9.2*).
- Aislar el iPhone y el portátil de la red sin apagarlos $\rightarrow$ **Punto 9 de la lista** (*ENFSI BPM §8.2 / RFC 3227 §3.2*).
- Pedir a Bahía que bloquee el usuario y usar fundas/aislamiento por temor al borrado remoto $\rightarrow$ **Punto 8 de la lista** (RFC 3227 §2.2 - Vías externas de cambio y deadman switches).
- Acudir a los logs del firewall, impresora, cámaras y a Bahía Sistemas $\rightarrow$ **Punto 11 de la lista** (*NIST SP 800-86 §3.1.1 - Identificación de fuentes y pivotaje*).
- Volcar la memoria RAM antes de clonar los discos físicos $\rightarrow$ **Puntos 16 y 17 de la lista** *(RFC 3227 §2.1 - Orden de volatilidad)*.
- Obtención de las imágenes forense de los dispositivos de almacenamiento no volátiles (*HDD*, *USB*, etc) $\rightarrow$ **Puntos 18 y 19 de la lista** *(RFC 3227 §2 / §2.1).*
