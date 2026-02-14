# Solución de Problemas - Minecraft NeoForge Server

## Error: "Incompatible client! Please use NeoForge 21.1.219"

Este error indica que tu cliente de Minecraft no tiene la misma versión de NeoForge que el servidor.

### Solución:

#### 1. Verificar la versión de NeoForge en tu cliente

Abre el Minecraft Launcher y verifica:

1. Ve a la pestaña "Instalaciones" (Installations)
2. Encuentra la instalación que usas para este servidor
3. Haz clic derecho y selecciona "Editar"
4. Verifica que la versión sea exactamente **NeoForge 21.1.219**

**Si no aparece exactamente 21.1.219:**

- Instala la versión específica desde: https://neoforgeed.net/
- Descarga NeoForge 21.1.219 para Minecraft 1.21.1
- Instálalo usando el instalador

#### 2. Verificar que estás usando la versión correcta de Minecraft

- El servidor usa **Minecraft 1.21.1**
- Tu cliente debe usar exactamente **Minecraft 1.21.1**
- No usar 1.21, 1.21.0, o 1.21.2 - debe ser 1.21.1 exactamente

#### 3. Sincronizar mods entre cliente y servidor

Si el servidor tiene mods instalados:

1. Copia todos los mods del directorio `minecraft-data/mods/` del servidor
2. Colócalos en la carpeta `mods` de tu instalación de Minecraft
3. Asegúrate de que las versiones de los mods sean las mismas

#### 4. Verificar que no hay mods de servidor sin cliente

Si hay mods en el servidor que son solo para servidor (server-side):
- Estos mods no necesitan estar en el cliente
- El archivo `neoforge-server.toml` debe estar configurado correctamente

## Error de conexión: "Connection refused"

### Verificar que Docker está corriendo

```bash
docker ps
```

Si Docker no está corriendo:
- Abre Docker Desktop
- Espera a que el icono de Docker esté activo

### Verificar que el puerto está disponible

```bash
# En Windows
netstat -an | findstr 25585
```

## Error de memoria: "Out of memory"

Aumentar la memoria en `.env`:

```
MINECRAFT_MAX_MEMORY=8G
MINECRAFT_INIT_MEMORY=2G
```

## El servidor no arranca

### Verificar logs

```bash
docker-compose logs mc
```

### Reiniciar completamente

```bash
docker-compose down
docker-compose up -d
```

### Eliminar mundo y empezar de cero

```
docker-compose down
rm -rf minecraft-data/world
docker-compose up -d
```

## Conexión desde otra red

### Configurar port forwarding en tu router

Redirige el puerto 25585 TCP a la IP de tu servidor.

### Usar tu IP pública

```bash
# Obtener IP pública
curl ifconfig.me
```

Conéctate usando: `tu-ip-publica:25585`

## Variables de entorno útiles

```
# Deshabilitar verificación de cuenta Mojang (para pruebas)
MINECRAFT_ONLINE_MODE=false

# Permitir vuelo (para modo creativo o mods)
allow-flight=true

# Aumentar distancia de visión (requiere más CPU)
MINECRAFT_VIEW_DISTANCE=12

# Aumentar jugadores máximos
MINECRAFT_MAX_PLAYERS=20
```

## Enlaces útiles

- [Documentación de itzg/minecraft-server](https://github.com/itzg/docker-minecraft-server)
- [NeoForge Downloads](https://neoforgeed.net/)
- [Minecraft Wiki](https://minecraft.wiki/)
