# Chat Distribuido con ZeroC Ice y Gradle Multimodulo

## Requisitos Previos

- **Java 17 o superior**
- **Gradle** instalado
- **ZeroC Ice** herramientas CLI (`slice2java`)
  - macOS: `brew install ice`
  - Ubuntu/Debian: `sudo apt install zeroc-ice-utils`
  - Windows: https://zeroc.com/downloads/ice

## Compilación

```bash
cd ice-chat-project
gradle build
```

## Ejecución (3 Terminales Diferentes)

### Terminal 1: SERVIDOR
```bash
gradle :server:run --console=plain
```

### Terminal 2: CLIENTE (Alice)
```bash
gradle :client:run --console=plain
```
Ingresa: `Alice`

### Terminal 3: CLIENTE (Bob)
```bash
gradle :client:run --console=plain
```
Ingresa: `Bob`

## Pruebas

**En Terminal 2 (Alice):**
```
> /users
>>> Usuarios activos (2): Alice, Bob
```

**En Terminal 3 (Bob):**
```
> Hola Alice
```

**En Terminal 2 (Alice):**
```
[14:35:20] <Bob>: Hola Alice
```

## Comandos CLI

| Comando | Descripción |
|---------|-------------|
| `/users` | Lista usuarios conectados |
| `/exit` | Desconectar |
| Cualquier texto | Enviar mensaje |

## Características Implementadas

✅ Gradle Multimodulo (common, server, client)
✅ Contrato Slice IDL
✅ Servidor Ice con Servant thread-safe
✅ Cliente interactivo con REPL
✅ Hilo receptor no-bloqueante
✅ Validación de nombres duplicados
✅ Desconexión limpia
✅ Manejo de excepciones distribuidas

---

**Curso:** Computación en Internet I (09810 - TIC)
**Institución:** Universidad Icesi
