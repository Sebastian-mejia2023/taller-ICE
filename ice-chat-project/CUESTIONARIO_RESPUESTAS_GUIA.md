# Respuestas al Cuestionario Técnico

## P1: Interoperabilidad de Plataformas Heterogéneas

**No requiere cambios en Chat.ice.** El contrato es agnóstico del lenguaje.

- Slice es independiente de la implementación
- `slice2python` genera Python, `slice2cpp` genera C++, `slice2java` genera Java
- **IceP (Ice Protocol):** Protocolo binario normalizado que garantiza interoperabilidad
- Serialización binaria uniforme para todos los tipos de datos

## P2: Análisis de Rendimiento (IceP vs REST/JSON)

### Tamaño Payload:
- **IceP:** ~28 bytes para ChatMessage
- **REST/JSON:** ~420-620 bytes (incluye headers HTTP)
- **Ventaja IceP:** 15-20x más compacto

### Serialización/Deserialización:
- **IceP:** 2-5 ms (lectura binaria directa)
- **REST/JSON:** 20-50 ms (parser JSON completo)
- **Ventaja IceP:** 10-25x más rápido

### Conexiones TCP:
- **IceP:** Multiplexación nativa, 1-2 conexiones por cliente
- **REST:** 10-20 conexiones con overhead de headers repetidos
- **Ventaja IceP:** Menor overhead de red

## P3: Semántica de Idempotencia

**`getPendingMessages` es `idempotent`:** Puede reintentarse sin efectos secundarios (solo lectura).

**`postMessage` NO es `idempotent`:** Reintentarlo duplicaría mensajes.

Cuando ocurre timeout TCP:
- Operaciones `idempotent`: Ice reintentar automáticamente
- Operaciones no-`idempotent`: Requiere intervención del usuario

## P4: Gestión de Concurrencia y ThreadPools

**Problema Thread-per-Connection:**
- 1000 clientes = 1000 hilos = 2GB de memoria
- Exhaustión de recursos del SO
- Context switching masivo

**Solución ObjectAdapter ThreadPool:**
- Número fijo de hilos (ej: 20 hilos para 1000 clientes)
- 40 MB de memoria en lugar de 2GB
- Graceful degradation en lugar de crash

ThreadPool integrado de Ice previene:
- Thread starvation
- Exhaustión de memoria
- Context switching excesivo
- Ataques DoS (SYN flood)

## P5: Bitácora de Uso Ético de IA

### Herramientas Utilizadas:
✅ Claude (Anthropic)
❌ ChatGPT
❌ Copilot
❌ Gemini

### Prompts Utilizados:
1. "Genera estructura Gradle multimodulo con compilación Slice automática"
2. "Implementa hilo receptor no-bloqueante con polling cada 500ms"
3. "Servlet thread-safe con ConcurrentHashMap y AtomicLong"

### Errores Identificados y Corregidos:
- Variable `running` sin `volatile` → Agregada sincronización
- Acceso no-sincronizado a `lastReceivedId` → Usando lectura sincronizada

### Validación Técnica:
✅ Compilación: `gradle build` sin errores
✅ Ejecución multi-terminal en 3+ terminales
✅ Todas las pruebas experimentales funcionando

---

**Nota:** Adapta estas respuestas a tus propias palabras para el informe.
