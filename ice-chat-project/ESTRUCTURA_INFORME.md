# ESTRUCTURA DEL INFORME TÉCNICO EN PDF

## PORTADA
```
UNIVERSIDAD ICESI
COMPUTACIÓN EN INTERNET I (09810 - TIC)
PERÍODO 2026-2

TALLER GUIADO: CHAT DISTRIBUIDO CON MIDDLEWARE ZEROC ICE

ESTUDIANTE 1: [Tu nombre]
ESTUDIANTE 2: [Nombre compañero]

FECHA: [Fecha]
```

## TABLA DE CONTENIDOS
1. Introducción
2. Descripción del Proyecto
3. Arquitectura y Diseño
4. Implementación (Archivos Clave)
5. Respuestas al Cuestionario Técnico
6. Pruebas Experimentales
7. Bitácora de Uso Ético de IA
8. Conclusiones

## SECCIÓN 1: INTRODUCCIÓN
- Contexto del middleware ZeroC Ice
- Objetivos del taller
- Tecnologías utilizadas (Gradle, Java 17, Ice 3.7.10)

## SECCIÓN 2: DESCRIPCIÓN DEL PROYECTO
Sistema de Chat Distribuido por Consola Multiusuario que permite:
- Login de usuarios
- Envío/recepción de mensajes
- Consulta de usuarios conectados
- Desconexión limpia

## SECCIÓN 3: ARQUITECTURA Y DISEÑO

### Componentes:
- **Common:** Contrato Slice + interfaces generadas
- **Server:** Implementación del Servant (ChatRoomI.java)
- **Client:** Cliente interactivo (ClientMain.java)

### Flujo:
```
Cliente → Proxy → IceP → Servidor → Servant → thread-safe data structures
```

## SECCIÓN 4: IMPLEMENTACIÓN

### Archivo 1: Chat.ice
Define: ChatMessage (struct), ChatRoom (interface), ChatException

### Archivo 2: ChatRoomI.java
- Concurrencia thread-safe con ConcurrentHashMap, AtomicLong
- Métodos sincronizados para login/logout
- Polling con getPendingMessages

### Archivo 3: ClientMain.java
- REPL interactivo
- Hilo demonio receptor (non-blocking)
- Polling cada 500ms

## SECCIÓN 5: RESPUESTAS AL CUESTIONARIO

### P1: Interoperabilidad
[Respuesta de CUESTIONARIO_RESPUESTAS_GUIA.md]

### P2: Rendimiento
[Respuesta de CUESTIONARIO_RESPUESTAS_GUIA.md]

### P3: Idempotencia
[Respuesta de CUESTIONARIO_RESPUESTAS_GUIA.md]

### P4: ThreadPools
[Respuesta de CUESTIONARIO_RESPUESTAS_GUIA.md]

### P5: Bitácora IAG
[Respuesta de CUESTIONARIO_RESPUESTAS_GUIA.md]

## SECCIÓN 6: PRUEBAS EXPERIMENTALES

### Test 1: Intercambio Bidireccional
[SCREENSHOT Terminal 2 (Alice) + Terminal 3 (Bob)]

### Test 2: Comando /users
[SCREENSHOT mostrando usuarios activos]

### Test 3: Rechazo de Nombres Duplicados
[SCREENSHOT del servidor rechazando nombre duplicado]

### Test 4: Desconexión Limpia
[SCREENSHOT del /exit funcionando]

### Test 5: Tolerancia a Fallos
[SCREENSHOT cuando servidor se detiene]

## SECCIÓN 7: BITÁCORA DE USO ÉTICO DE IA

### Herramientas:
✅ Claude (Anthropic)

### Prompts:
[Listar prompts utilizados]

### Errores Corregidos:
[Listar errores que IA cometió y tú corregiste]

### Validación:
✅ Compilación exitosa
✅ Pruebas multi-terminal
✅ Todos los comandos funcionan

## SECCIÓN 8: CONCLUSIONES
- Logros alcanzados
- Lecciones aprendidas
- Trabajo futuro

---

**TOTAL: 15-20 páginas**
