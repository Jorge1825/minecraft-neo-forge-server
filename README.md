# Minecraft NeoForge Server

Servidor de Minecraft con NeoForge montado con Docker Compose.

## Estructura de directorios

```
.
├── docker-compose.yml      # Configuración de Docker Compose
├── .env.example           # Variables de entorno de ejemplo
├── .gitignore             # Archivos ignorados por Git
└── minecraft-data/        # Datos del servidor (volumen Docker)
    ├── mods/              # Mods del servidor (NeoForge)
    ├── world/             # Mundo del servidor
    └── config/            # Configuraciones adicionales
```

## Configuración inicial

1. Copia el archivo de entorno de ejemplo:
```bash
cp .env.example .env
```

2. Edita el archivo `.env` con tus preferencias:
   - Cambia `PORT` si necesitas un puerto diferente
   - Ajusta `MINECRAFT_VERSION` para la versión deseada
   - Modifica `MINECRAFT_MAX_PLAYERS` según necesites
   - Configura `SERVICE_PASSWORD_RCON` con una contraseña segura

## Uso

### Iniciar el servidor
```bash
docker-compose up -d
```

### Ver logs del servidor
```bash
docker-compose logs -f mc
```

### Detener el servidor
```bash
docker-compose down
```

### Reiniciar el servidor
```bash
docker-compose restart mc
```

## Mods

Para agregar mods al servidor:
1. Coloca los archivos `.jar` de los mods en el directorio `minecraft-data/mods/`
2. Reinicia el servidor para que los mods se carguen

**Nota:** Asegúrate de que los mods sean compatibles con la versión de NeoForge especificada en `FORGE_VERSION`.

## Acceso a la consola

Para acceder a la consola del servidor:
```bash
docker-compose exec mc rcon-cli
```

## Variables de entorno importantes

| Variable | Descripción | Por defecto |
|----------|-------------|-------------|
| `PORT` | Puerto del servidor | 25565 |
| `MINECRAFT_VERSION` | Versión de Minecraft | latest |
| `MINECRAFT_TYPE` | Tipo de servidor | FORGE |
| `FORGE_VERSION` | Versión de NeoForge | 21.1.219 |
| `MINECRAFT_MAX_PLAYERS` | Jugadores máximos | 10 |
| `MINECRAFT_MAX_MEMORY` | Memoria máxima | 1G |
| `MINECRAFT_DIFFICULTY` | Dificultad (peaceful, easy, normal, hard) | normal |
| `MINECRAFT_GAME_MODE` | Modo de juego (survival, creative, adventure, spectator) | survival |
| `MINECRAFT_ONLINE_MODE` | Verificación de cuentas Mojang | true |
