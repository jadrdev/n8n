# n8n Docker Setup

## Despliegue en Render

### Pasos:

1. **Sube el proyecto a GitHub**
   ```bash
   git init
   git add .
   git commit -m "Initial n8n setup"
   git branch -M main
   git remote add origin <tu-repo-url>
   git push -u origin main
   ```

2. **Despliega en Render**
   - Ve a [render.com](https://render.com)
   - Inicia sesión con GitHub
   - Click en "New +" → "Blueprint"
   - Conecta tu repositorio
   - Render detectará automáticamente el `render.yaml`
   - Click en "Apply"

3. **Configura Supabase**
   - Ve a tu proyecto en Supabase
   - En Settings → Database, copia la cadena de conexión
   - Obtendrás: host, database, user, password

4. **Configura las variables de entorno en Render**
   Después del despliegue, ve a tu servicio y actualiza:
   - `N8N_HOST`: copia el dominio que te dio Render (ej: `n8n-xxxx.onrender.com`)
   - `WEBHOOK_URL`: `https://tu-dominio.onrender.com/`
   - `N8N_EDITOR_BASE_URL`: `https://tu-dominio.onrender.com`
   - `N8N_BASIC_AUTH_PASSWORD`: cambia la contraseña si quieres
   - `DB_POSTGRESDB_HOST`: host de Supabase (ej: `db.xxx.supabase.co`)
   - `DB_POSTGRESDB_DATABASE`: nombre de la base de datos (normalmente `postgres`)
   - `DB_POSTGRESDB_USER`: usuario de Supabase (normalmente `postgres`)
   - `DB_POSTGRESDB_PASSWORD`: contraseña de tu base de datos Supabase

5. **Accede a tu n8n**
   - Usa el dominio generado: `https://n8n-xxxx.onrender.com`
   - Usuario: `admin`
   - Contraseña: la que configuraste o la generada automáticamente

**Nota:** El plan gratuito de Render tiene 750 horas/mes y el servicio se suspende tras 15 minutos de inactividad (tarda ~1 min en despertar).

## Uso Local

```bash
docker-compose up -d
```

Accede en: http://localhost:5678

**Credenciales por defecto:**
- Usuario: admin
- Contraseña: changeme
