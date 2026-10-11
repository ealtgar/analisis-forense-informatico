#### FASE 1: Preparación y llegada a la escena (Antes de actuar)

- [ ] 1. ¿Se ha verificado que el equipo técnico, software forense en soportes de solo lectura y material de embalaje (fundas Faraday, bolsas anti-ESD) están disponibles y operativos? *(ENFSI BPM §9.1)*
- [ ] 2. ¿Se conocen los límites legales de la actuación, las políticas corporativas aplicables y lo que dicta la orden judicial/contrato? _(NIST SP 800-86 §3.1.1 / ENFSI BPM §9.1)_
- [ ] 3. Al llegar: ¿Se ha apartado inmediatamente a los sospechosos y testigos de los equipos y de cualquier dispositivo con capacidad de conexión remota? _(ENFSI BPM §8.2)_
#### FASE 2: Evaluación inicial y aseguramiento (Antes de tocar nada)

- [ ] 4. ¿Es necesaria la intervención de peritos de otras disciplinas (ADN, dactiloscopia)? En caso afirmativo, ¿hemos acordado el orden de intervención para no destruir pruebas físicas? _(ENFSI BPM §8.2 / §9.1)_
- [ ] 5. ¿Se ha documentado el estado general de la escena mediante fotografías exhaustivas y un croquis detallado de la ubicación de cada equipo y sus conexiones? _(ENFSI BPM §8.2)_
- [ ] 6. ¿Hay periféricos, memorias USB, teléfonos, cámaras u otros dispositivos portátiles que deban incluirse en la incautación? _(NIST SP 800-86 §3.1.1 / ENFSI BPM §9.2)_
- [ ] 7. ¿Se ha identificado cuáles sistemas están encendidos y cuáles apagados? **(IMPORTANTE: Si está encendido, NO APAGAR TODAVÍA)**. _(RFC 3227 §2.2 / ENFSI BPM §9.2)_
#### FASE 3: Toma de decisiones e identificación de fuentes

- [ ] 8. ¿Existe riesgo de que el aislamiento brusco dispare un _deadman switch_ (borrado automático) del malware? _(RFC 3227 §2.2 / §3.2)_
- [ ] 9. Si no hay riesgo de borrado automático, ¿Se ha eliminado las vías de cambio externo aislándolo de la red (desconexión física o fundas inhibidoras de RF verificadas)? _(ENFSI BPM §8.2 / RFC 3227 §3.2)_
- [ ] 10. ¿Se ha listado formalmente todos los sistemas implicados sobre los que se va a adquirir evidencia? _(RFC 3227 §3.2)_
- [ ] 11. ¿Se ha identificado fuentes externas necesarias que documenten el incidente (logs centralizados, servidores departamentales, tráfico de firewalls/IDS, datos del ISP)? _(NIST SP 800-86 §3.1.1)_
- [ ] 12. ¿Se ha verificado si las políticas de la organización me autorizan legalmente a adquirir los dispositivos de empleados o ajenos a la organización (BYOD)? _(NIST SP 800-86 §3.1.1)_
#### FASE 4: Ejecución y orden de adquisición (Trabajo en equipo)

- [ ] 13. ¿Se ha anotado la hora que muestra el reloj del sistema y calculado el desfase exacto respecto a la hora UTC real? _(RFC 3227 §2 / §3.2)_
- [ ] 14. ¿Se está ejecutando herramientas de recolección fiables desde _nuestros propios soportes físicos_ en lugar de usar los binarios/programas del sistema comprometido? _(RFC 3227 §2.2)_
- [ ] 15. ¿Nos estamos absteniendo de usar comandos que alteren de forma masiva los tiempos de acceso (_atime_) de los archivos (ej. `tar`, `xcopy`, exploradores de Windows)? _(RFC 3227 §2.2)_
- [ ] 16. **[PRIORIDAD 1]** ¿Se ha volcado el estado de las conexiones, tabla de procesos, caché ARP y estadísticas del kernel? _(RFC 3227 §2.1 / §3.2)_
- [ ] 17. **[PRIORIDAD 2]** ¿Se ha capturado íntegramente la memoria RAM en busca de claves, cifrado en vivo y malware sin dejar rastro en disco? _(RFC 3227 §2.1 / ENFSI BPM §9.1 / NIST SP 800-86 §3.1.1)_
- [ ] 18. **[PRIORIDAD 3]** ¿Se ha realizado la imagen forense (*copia bit a bit*) del disco duro físico tras terminar de recoger los datos volátiles? _(RFC 3227 §2 / §2.1)_
- [ ] 19. **[PRIORIDAD 4]** ¿Se ha asegurado y copiado otras fuentes menos volátiles (logs remotos en otros servidores, configuraciones físicas de red, cintas de backup y soportes CD/DVD/USB)? _(RFC 3227 §2.1)_
#### FASE 5: Preservación, Documentación y Cadena de Custodia

- [ ] 20. ¿Se ha generado las sumas de verificación (_hashes_ criptográficos) de todas las copias de evidencia recolectadas en el sistema para garantizar su inalterabilidad? _(RFC 3227 §3.2)_
- [ ] 21. ¿Están todos los soportes lógicos generados debidamente replicados? (Trabajar sobre la copia de la copia, no sobre la original). _(RFC 3227 §2)_
- [ ] 22. ¿Se ha embalado los equipos físicos utilizando medidas anti-ESD y material que los proteja de golpes, campos magnéticos, vibraciones y cambios de temperatura? _(ENFSI BPM §8.2)_
- [ ] 23. ¿Se ha etiquetado **cada artículo incautado** con su identificador único, descripción precisa (números de serie), lugar de hallazgo, fecha/hora y mi nombre y firma? _(ENFSI BPM §8.2)_
- [ ] 24. ¿Las notas son metódicas, registran todos los pasos y comandos ejecutados, y están fechadas y firmadas para permitirnos testificar con fiabilidad años después? _(RFC 3227 §2)_
