```markdown
# mAntiRaid

mAntiRaid es un plugin pensado para reducir y bloquear raideos y spam en servidores de Minecraft.  
Nota importante: este plugin NO pretende reemplazar sistemas anti-hack ni detección avanzada de cheaters. Su objetivo principal es mitigar ataques masivos (raids) y comportamientos abusivos que afectan la experiencia de juego para la mayoría de los servidores.

Descripción rápida
- Protege contra entradas masivas de jugadores, spam en chat, spam de comandos y otros patrones típicos de raideos.
- Fácil de configurar y ajustar a la necesidad del servidor.
- Mensajes y acciones personalizables.

Características sugeridas (lista de funciones)
Estas son ideas de funciones (con nombres amigables) que puedes implementar en el plugin. Te doy la descripción de qué bloquea cada una y cómo se comporta de forma amigable:

- Protección de "Ingreso Masivo" (Mass Join Protector)
  - ¿Qué bloquea? Entradas rápidas y simultáneas de muchos usuarios (ej. decenas de cuentas intentando unirse en segundos).
  - Acción típica: bloquear nuevas entradas temporalmente, notificar staff, activar lista blanca temporal.

- Límite de tasa de unión (Join Rate Limit)
  - ¿Qué bloquea? Ráfagas de conexiones desde la misma IP o rango en poco tiempo.
  - Acción típica: kick temporal por IP, añadir a lista de sospechosos.

- Enfriamiento de chat (Chat Cooldown)
  - ¿Qué bloquea? Mensajes repetidos en el chat por parte de un mismo jugador (spam).
  - Acción típica: ignorar mensajes repetidos, warning, mute temporal.

- Detección de mensajes idénticos (Anti-Repeat)
  - ¿Qué bloquea? Flood de mensajes idénticos en poco tiempo (copiar-pegar).
  - Acción típica: cancelar mensaje y aumentar contador de advertencias.

- Bloqueo de comandos en ráfaga (Command Flood Protection)
  - ¿Qué bloquea? Uso masivo de comandos por parte de cuentas (por ejemplo, /warp /tpa repetidos).
  - Acción típica: negar ejecución durante un cooldown por jugador.

- Protección contra spawns masivos de entidades (Mass Entity Spawn Protection)
  - ¿Qué bloquea? Generación agresiva de mobs o entidades para laguear el servidor.
  - Acción típica: cancelar el spawn en exceso, notificar staff.

- Protección TNT / Explosivos en masa (Explosive Throttle)
  - ¿Qué bloquea? Colocación o detonación masiva de TNT/creepers para causar lag o grief.
  - Acción típica: limitar explosiones por segundo por región, cancelar detonaciones masivas.

- Protección de items (Item Drop/Item Spam Filter)
  - ¿Qué bloquea? Tirar grandes cantidades de items para saturar chunk/entities.
  - Acción típica: impedir drop masivo o deshabilitar drops de items por usuarios sospechosos.

- Auto-lock servidor (Emergency Lockdown)
  - ¿Qué bloquea? En caso de detección de raid activo detiene nuevas conexiones y puede cambiar el servidor a modo mantenimiento.
  - Acción típica: bloquear dals joins, enviar mensajes a todos los administradores.

- Baneo / Kick Automático Basado en Umbrales (Auto Punishment)
  - ¿Qué bloquea? Jugadores que exceden repetidamente límites de spam o comportamiento.
  - Acción típica: warnings -> mute -> kick -> ban temporal/perm.

- Registro y notificación (Logging & Alerts)
  - ¿Qué bloquea? No bloquea por sí mismo, pero registra eventos sospechosos y notifica a staff por chat/console o via webhook (opcional).
  - Acción típica: log detallado con hora, IP, acción tomada; notificación a discord/webhook.

Ejemplo de opciones de configuración sugeridas (config.yml)
```yaml
# Ejemplo de configuración
join:
  threshold_per_10s: 10     # cantidad de joins en 10s que dispara protección
  ip_ban_duration_minutes: 60

chat:
  cooldown_seconds: 2       # segundos mínimos entre mensajes por jugador
  max_identical_in_window: 3
  warning_before_mute: 2

commands:
  cooldown_seconds: 1

entities:
  max_spawns_per_chunk_per_minute: 50

explosives:
  max_explosions_per_second: 3

logging:
  enable_discord_webhook: false
  webhook_url: ""
```

Comandos sugeridos (ejemplos)
- /mantaraid reload — recarga la configuración del plugin.
- /mantaraid status — muestra el estado y contadores actuales.
- /mantaraid toggle — activa/desactiva temporalmente las protecciones.
- /mantaraid whitelist add <jugador|ip> — añadir a whitelist para evitar bloqueos.
- /mantaraid lockdown enable/disable — forzar modo lockdown.

Permisos sugeridos
- mantaraid.admin — Permiso completo para administrar el plugin.
- mantaraid.view — Ver el estado y logs.
- mantaraid.whitelist — Gestionar la whitelist.

Mensajes y experiencia amigable
- Mensajes en español claros y cortos, por ejemplo:
  - "Protección activada: demasiadas conexiones simultáneas. Inténtalo de nuevo en unos minutos."
  - "Has sido silenciado temporalmente por enviar mensajes repetidos."
  - "Acción automática: jugador expulsado por comportamiento sospechoso."

Notas y recomendaciones
- Prueba los límites en un servidor de pruebas antes de aplicarlo en producción.
- Ajusta thresholds según la media de tus jugadores (número real de jugadores concurrentes).
- Todo bloqueo debe ser claro para el usuario final: mostrar el motivo del kick/mute y el tiempo.
- No confíes únicamente en este plugin para seguridad anti-cheat; combínalo con herramientas específicas de anticheat.

Contribuciones
- Si quieres que redacte textos para los mensajes del plugin, ejemplos de config comentada o incluso implementar comandos/config por defecto, dime y lo preparo.
- Puedes implementar las funciones siguiendo los nombres amigables arriba propuestos; si quieres te armo plantillas de código o ejemplos de eventos a escuchar.

Licencia y contacto
- Añade la licencia que prefieras (MIT, GPL, etc.).  
- Contacto: @ElMichiDe (en GitHub) para dudas y mejoras.

---

He actualizado este README proponiendo una descripción extendida, una lista de funciones amigables con lo que cada una bloquea, ejemplos de configuración, comandos y recomendaciones. Si quieres, puedo:
- Preparar un commit con este README actualizado en la rama que indiques, o
- Generar ejemplos de implementación (plantillas de eventos en Java/Bukkit/Spigot/Paper) para cada una de las funciones listadas.

Dime qué prefieres que haga a continuación y lo hago.
```
