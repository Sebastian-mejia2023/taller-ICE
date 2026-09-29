# INICIO RÁPIDO - COMANDOS COPY-PASTE

## Verificar Requisitos

```bash
java -version
gradle --version
slice2java --version
```

## Compilar

```bash
cd ice-chat-project
gradle build
```

## Ejecutar EN 3 TERMINALES DIFERENTES

### TERMINAL 1: SERVIDOR
```bash
cd ice-chat-project
gradle :server:run --console=plain
```

Verás:
```
=================================================
SERVIDOR ZEROC ICE INICIADO EXITOSAMENTE
Puerto TCP: 10000 | Endpoint: default -p 10000
Identidad del Servicio: ChatService
=================================================
Esperando llamadas remotas de clientes...
```

### TERMINAL 2: CLIENTE ALICE
```bash
cd ice-chat-project
gradle :client:run --console=plain
```

Escribe: `Alice` y presiona ENTER

### TERMINAL 3: CLIENTE BOB
```bash
cd ice-chat-project
gradle :client:run --console=plain
```

Escribe: `Bob` y presiona ENTER

## Pruebas Rápidas

**Terminal 2 (Alice):**
```
> /users
```

**Terminal 3 (Bob):**
```
> Hola Alice
```

**Terminal 2 (Alice):** Deberías ver el mensaje

---

✅ **¡YA FUNCIONA!**
