# Red de Comunicaciones Mesh LoRa 915 MHz
## Propuesta Técnica — Radio Club LU4BB

**Presentado a la Comisión Directiva del LU4BB**  
Buenos Aires, septiembre de 2026  
*Versión 1.0 — Para revisión y aprobación de la CD*

---

## 1. El Problema: Cuando las Comunicaciones Colapsan

> **Caso real — Bahía Blanca, 7 de marzo de 2025:** En menos de 9 horas cayeron más de 300 mm de lluvia — cuatro veces el récord histórico de la ciudad. El resultado: 16 muertos, más de 5.000 evacuados, 12.000 hogares sin electricidad, y la red celular completamente colapsada. Los vecinos quedaron incomunicados. Los servicios de emergencia no podían recibir llamados. El sistema 911 colapsó. Las empresas Personal y Flow debieron activar de urgencia una "Red Libre de Emergencia" por internet — pero sin luz, esa red tampoco funcionaba.

No fue un hecho aislado. El 16 de diciembre de 2023, un tornado arrasó Bahía Blanca con vientos que destruyeron el techo del Club Bahiense del Norte durante un evento deportivo, matando a 13 personas. En ambos casos el patrón se repitió: la infraestructura centralizada — celular, internet, electricidad — colapsó exactamente en el momento en que más se la necesitaba.

El problema estructural es siempre el mismo: las redes de comunicación modernas dependen de infraestructura centralizada — antenas celulares, servidores, tendido eléctrico. Cuando una catástrofe golpea, esa infraestructura es la primera en caer.

> **¿Qué hubiera cambiado con una red Meshtastic activa?** Una red mesh LoRa no tiene punto central de falla. No depende de la luz eléctrica, no depende de internet, no depende de servidores. Cada nodo es autónomo. Si cae uno, los demás siguen operando. Si cae la luz, los nodos solares siguen activos por días. Es exactamente el tipo de infraestructura que se necesita cuando todo lo demás falla.

### 1.1 Antecedente directo: la UNS ya lo está haciendo en Bahía Blanca

El 31 de agosto de 2026 la Universidad Nacional del Sur (UNS) puso en operación un nodo público de la red Meshtastic en el edificio de Agronomía de su campus de Palihue, uno de los puntos más altos de Bahía Blanca. La iniciativa surgió directamente como respuesta a los cortes de comunicación experimentados durante los temporales de 2023 y 2025.

> *"Más que una alternativa al teléfono celular o las radios VHF, esto propone algo diferente: una red de comunicaciones que puede seguir funcionando cuando las redes convencionales dejan de hacerlo. Su fortaleza no está solamente en el alcance de cada dispositivo, sino en que cada nodo puede convertirse en parte de una infraestructura distribuida, de bajo consumo, relativamente económica y sin un punto central cuya caída deje incomunicado al resto."*
> — Ing. Mariano Coccia, Dirección General de Telecomunicaciones, UNS / Sudoeste Mesh

La red comunitaria **Sudoeste Mesh**, que instaló el nodo en la UNS, ya cubre Bahía Blanca y alcanza Sierra de la Ventana, Coronel Dorrego, Monte Hermoso y Tres Arroyos. Ofrece retransmisión de alertas del Servicio Meteorológico Nacional, datos de sensores ambientales y seguimiento de nodos móviles.

Este antecedente es especialmente significativo: proviene de la misma ciudad afectada por los cortes que motivaron esta propuesta, involucra a una universidad nacional como primera adoptante, y confirma que la tecnología ya está siendo usada en Argentina en el contexto exacto de emergencias climáticas. El artículo también menciona que Argentina cuenta con un proyecto financiado internacionalmente para llevar esta tecnología a brigadas de bomberos forestales.

---

## 2. La Propuesta

La comunidad Meshtastic Argentina solicita a la Comisión Directiva del Radio Club LU4BB autorización para instalar un único nodo autónomo de prueba sobre infraestructura del club, con el objetivo de:

- Validar el alcance real de la red Meshtastic sobre el área metropolitana de Buenos Aires desde un punto de altura privilegiado.
- Establecer el primer nodo backbone de una red de comunicaciones de emergencia descentralizada para la Ciudad de Buenos Aires y el Gran Buenos Aires.
- Posicionar al LU4BB como institución pionera en infraestructura alternativa de emergencia, reforzando el rol histórico de la radioafición como servicio a la comunidad.

> **Compromiso de costos:** La comunidad Meshtastic Argentina asume la totalidad de los costos del proyecto — hardware, instalación, mantenimiento y reposición. El LU4BB no incurre en ningún gasto ni adquiere ninguna obligación económica. Lo único que se solicita es la autorización para usar un punto de altura en la infraestructura del club.

---

## 3. La Tecnología

### 3.1 ¿Qué es Meshtastic?

Meshtastic es una plataforma de comunicaciones de código abierto basada en radios LoRa (Long Range Radio) que crea redes malladas (mesh) descentralizadas, cifradas y capaces de operar sin internet, sin torres celulares y sin energía de red.

Cada nodo actúa simultáneamente como receptor y repetidor: retransmite automáticamente los mensajes de otros nodos para extender el alcance de la red sin ninguna configuración manual. Los mensajes viajan cifrados con AES-128. La aplicación móvil (iOS y Android, gratuita) se conecta al nodo vía Bluetooth. No requiere suscripción, cuenta ni ningún servicio externo.

### 3.2 ¿Por qué la banda de 915 MHz?

La banda ISM de 915 MHz está autorizada en Argentina por la **Resolución ENACOM 7/2005** (ex-CNC) para uso libre sin habilitación individual, dentro de los límites de potencia establecidos. No se requiere licencia de radioaficionado. Los equipos propuestos cuentan con certificación FCC y CE.

Esta banda es la recomendada para Meshtastic en la Región 2 de la UIT (Américas) y opera en un espectro completamente distinto al de radioafición, por lo que no interfiere con ninguna actividad existente del club.

### 3.3 Complementariedad con APRS y las actividades del club

Esta iniciativa no reemplaza ni compite con las actividades del LU4BB. Aporta capacidades que APRS no tiene:

| Característica | APRS | Meshtastic LoRa |
|---|---|---|
| Cifrado | ❌ Texto plano | ✅ AES-128 |
| Requiere internet | ✅ (iGates) | ❌ 100% offline |
| Licencia requerida | ✅ Radioaficionado | ❌ Banda ISM libre |
| GPS tiempo real grupal | Limitado | ✅ Nativo |
| Telemetría de sensores | Limitado | ✅ Nativo |

Ambas tecnologías son complementarias: en una emergencia, APRS conecta con la red global de radioaficionados; Meshtastic conecta localmente sin depender de nada externo.

---

## 4. Cobertura Estimada

La ventaja de un nodo en altura es directa: el horizonte de radio se calcula como `4,12 × √altura (metros)`. A mayor altura, mayor radio de cobertura sin obstáculos. Un punto de instalación elevado en la infraestructura del club permitiría cubrir:

- **Norte:** toda CABA, zona norte del conurbano, Tigre y el Delta.
- **Sur/Sureste:** La Plata, Quilmes, Avellaneda y el corredor de la Ruta 2.
- **Oeste:** GBA oeste — Lomas de Zamora, Lanús, Morón.
- **Este:** Río de la Plata con señal de largo alcance sobre agua libre.

Un único nodo bien posicionado en altura vale más que decenas de nodos al nivel del piso: reduce los saltos necesarios, disminuye la saturación del canal y mejora la tasa de entrega de paquetes.

---

## 5. Uso en Emergencias Urbanas

### 5.1 Escenario: Colapso total de redes (el escenario Bahía Blanca)

Tormenta severa, inundación, apagón extendido o cualquier evento que derribe la red celular y el suministro eléctrico. En ese momento:

- El nodo del club, alimentado por panel solar y batería de 13.400 mAh, permanece operativo **más de 9 días sin sol** y de forma indefinida con exposición solar mínima.
- Los socios y voluntarios equipados con nodos portátiles (~USD 25 cada uno) pueden comunicarse entre sí y con el puesto de comando del club sin celular, sin internet, sin luz de red.
- Los mensajes viajan cifrados: solo los miembros del grupo con el canal configurado pueden leerlos.
- El puesto de comando ve en tiempo real la posición GPS de todos los equipos desplegados en el terreno.

> **Diferencia crítica respecto al caso Bahía Blanca:** En marzo de 2025, los vecinos y servicios de emergencia quedaron incomunicados porque todas sus herramientas dependían de infraestructura centralizada (celular, internet, 911). Una red Meshtastic activa hubiera permitido comunicación local inmediata entre vecinos, voluntarios y Defensa Civil, sin depender de nada externo.

### 5.2 Escenario: Búsqueda y rescate

- Cada equipo de terreno lleva un nodo portátil y comparte su posición GPS en tiempo real con el puesto de comando, sin necesidad de celular ni internet.
- El puesto de comando ve a todos los equipos simultáneamente en el mapa de la app Meshtastic.
- Compatible con equipos de Defensa Civil, Bomberos y Cruz Roja mediante distribución de nodos con el mismo canal configurado.

### 5.3 Protocolo de activación

| Nivel | Estado | Acción |
|---|---|---|
| 0 | Normal | Red activa en monitoreo. Socios pueden usarla para comunicación cotidiana y pruebas. |
| 1 | Alerta | Socios de guardia activan nodos portátiles adicionales. Verificación de cobertura en zonas de riesgo. |
| 2 | Emergencia | Distribución de nodos a grupos de respuesta. Puesto de comando activado en sede del club. Coordinación con Defensa Civil. |
| 3 | Desastre | Apertura del canal para uso comunitario. Difusión del punto de acceso entre la población afectada. |

---

## 6. Hardware Propuesto

| Parámetro | SenseCAP Solar P1-Pro (nodo fijo) | Heltec WiFi LoRa V4 (nodo portátil) |
|---|---|---|
| Banda | 915 MHz ISM — libre sin licencia | 915 MHz ISM — libre sin licencia |
| Potencia TX | 22 dBm (SX1262) | 28 dBm (SX1262 HP) |
| Sensibilidad RX | −137 dBm (SF12) | −137 dBm (SF12) |
| Alcance campo | 8–9 km entre nodos | 5–8 km entre nodos |
| Energía | Solar 5W + 4×18650 = 13.400 mAh | Batería LiPo externa |
| Autonomía sin sol | > 9 días | Variable |
| Impermeabilidad | IPX5 | Con carcasa impresa |
| GPS integrado | Sí — GPS / GLONASS / Galileo | Opcional externo |
| Cifrado | AES-128 | AES-128 |
| Firmware | Meshtastic (pre-instalado) | Meshtastic (flash manual) |
| Precio estimado | ~USD 90 | ~USD 25 |

### El nodo fijo — SenseCAP Solar Node P1-Pro

- Alimentación 100% solar con panel de 5W y batería de 13.400 mAh — **sin cables de electricidad**, sin intervención en la instalación eléctrica del club.
- Dimensiones compactas (191 × 201 × 42 mm) con kit de montaje en mástil incluido — instalación en menos de 30 minutos.
- IPX5: resiste lluvia y agua a presión — apto para exterior permanente.
- GPS integrado para sincronización temporal del mesh y reporte de posición como nodo fijo de referencia.
- Interface Grove para expansión con sensores ambientales: puede funcionar también como **estación meteorológica del club**, transmitiendo temperatura, humedad y presión sobre el mesh.
- **Desmontable en 15 minutos** sin dejar rastro si la CD decide retirarlo.

---

## 7. Compromisos

### Lo que asume la comunidad Meshtastic Argentina (todo):

- Adquisición, importación e instalación del hardware. Costo estimado: ~USD 90.
- Traslado al club y montaje en fecha coordinada con la CD.
- Mantenimiento, actualizaciones de firmware y reposición en caso de falla.
- Informe técnico de cobertura para compartir con la CD y la comunidad de radioaficionados.
- Toda coordinación logística y técnica, sin requerir personal del club.

### Lo que se solicita al LU4BB (únicamente):

- Aprobación de la CD para instalar un nodo autónomo solar en un punto de altura de la infraestructura del club, con fines de prueba de despliegue de red Meshtastic.
- Autorización de acceso para que un técnico de la comunidad realice el montaje en fecha acordada (operación de aprox. 30 minutos).

> **En síntesis:** No se solicita dinero, no se solicita personal técnico del club, ni se genera ninguna obligación permanente. Solo se solicita la autorización de la CD para usar un punto elevado de la infraestructura del club en un proyecto que beneficia directamente a la institución y a la comunidad.

---

## 8. Plan de Implementación

Todos los costos son absorbidos íntegramente por la comunidad Meshtastic Argentina.

| Fase | Descripción | Hardware | Plazo | Costo |
|---|---|---|---|---|
| **1 – Piloto** *(esta propuesta)* | Nodo ROUTER en infraestructura del club. Validación de cobertura real sobre Buenos Aires. | SenseCAP P1-Pro × 1 | 1 mes | ~USD 90 *(comunidad)* |
| **2 – Backbone** | Nodos ROUTER en puntos altos estratégicos: Parque Chacabuco, Parque Centenario, Costanera Norte, GBA. | SenseCAP P1-Pro × 3 | 3 meses | ~USD 270 *(comunidad)* |
| **3 – Emergencias** | Nodos portátiles distribuidos a grupos de emergencia, Defensa Civil y radioaficionados de guardia. | Heltec V4 × 10 | 3 meses | ~USD 250 *(comunidad)* |
| **4 – Expansión** | Crecimiento orgánico. Nuevos nodos de socios y colaboradores. MQTT opcional para monitoreo. | Variable | Continuo | Autofinanciado |

---

## 9. Marco Regulatorio

- **Resolución ENACOM 7/2005** (ex-CNC): autoriza dispositivos de baja potencia en banda ISM 902–928 MHz sin habilitación individual.
- Los equipos propuestos cuentan con certificación FCC y CE y operan dentro de los límites de potencia permitidos.
- No se requiere licencia de radioaficionado para operar en la banda ISM de 915 MHz.

---

## 10. Próximos Pasos

**Se solicita a la Comisión Directiva:**

- [ ] Aprobar la instalación del nodo autónomo en infraestructura del club mediante acta de reunión de CD.
- [ ] Acordar con el referente de la comunidad Meshtastic Argentina el punto de instalación y fecha de montaje.

**La comunidad Meshtastic Argentina se encargará de:**

- [ ] Adquisición e importación del hardware (sin costo para el club).
- [ ] Instalación en la fecha acordada.
- [ ] Informe de cobertura a la CD dentro de los 30 días posteriores a la puesta en marcha.
- [ ] Articulación en etapas siguientes con Defensa Civil, Bomberos y otros organismos de emergencia.

---

## Referencias

**[1]** Dirección de Comunicación UNS. *"La UNS se sumó al nodo público de comunicaciones de emergencia que se extiende por la región."* Enfoque U — Universidad Nacional del Sur, Bahía Blanca. 31 de agosto de 2026.  
🔗 https://www.enfoqueu.uns.edu.ar/la-uns-se-sumo-al-nodo-publico-de-comunicaciones-de-emergencia-que-se-extiende-por-la-region/

**[2]** Municipio de Bahía Blanca. *"Temporal 7 de marzo de 2025."* 300+ mm en 9 horas — récord histórico absoluto. 16 fallecidos, más de 5.000 evacuados, red celular y sistema 911 colapsados.

**[3]** Municipio de Bahía Blanca. *"Temporal 16 de diciembre de 2023 — Tornado."* Derrumbe del techo del Club Bahiense del Norte. 13 fallecidos.

**[4]** Meshtastic Project. *"Meshtastic — An open source, off-grid, decentralized, mesh network."* Documentación técnica oficial. 2024–2026.  
🔗 https://meshtastic.org

**[5]** ENACOM (ex-CNC). *"Resolución 7/2005 — Equipos de Radiocomunicaciones de Baja Potencia."* Autorización de uso de bandas ISM en Argentina, incluida la banda 902–928 MHz, sin necesidad de habilitación individual.

**[6]** Seeed Studio. *"SenseCAP Solar Node P1-Pro for Meshtastic — Ficha técnica."* 2025–2026.  
🔗 https://www.seeedstudio.com/SenseCAP-Solar-Node-P1-Pro-for-Meshtastic-LoRa-p-6412.html

**[7]** Sudoeste Mesh. *"Red comunitaria de comunicaciones de emergencia — Bahía Blanca y región."*  
🔗 Instagram: [@sudoestemesh](https://instagram.com/sudoestemesh) | GitHub: [github.com/sudoestemesh](https://github.com/sudoestemesh)

---

*Propuesta elaborada por la comunidad Meshtastic Argentina con el respaldo del Radio Club LU4BB.*
