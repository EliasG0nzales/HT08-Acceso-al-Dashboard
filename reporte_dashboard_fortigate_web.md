# Reporte de Funcionalidad del Dashboard FortiGate Web

## 1. Descripción general

El dashboard FortiGate Web es un panel de control orientado a la administración del filtrado web corporativo. Su objetivo es centralizar la supervisión del tráfico HTTP/HTTPS, la gestión de políticas, usuarios, categorías FortiGuard, listas URL, cuotas de navegación, alertas, logs y configuración del sistema.

La interfaz simula un entorno FortiGate/FortiOS para mostrar cómo una organización puede controlar qué sitios se permiten, bloquean, monitorean o limitan según reglas de seguridad, productividad y cumplimiento.

## 2. Funcionamiento general de la interfaz

El sistema inicia con una pantalla de login. Después de autenticarse, muestra una pantalla de carga con video y luego abre el dashboard principal.

El dashboard se divide en:

- Menú lateral: permite navegar entre los módulos.
- Barra superior: muestra el título del módulo activo, buscador global, acceso rápido a logs y botón de actualización.
- Área central: muestra el contenido de cada panel.
- Widgets y gráficas: presentan métricas, tendencias y distribución de eventos.
- Sistema de notificaciones: muestra mensajes tipo toast cuando se aplican filtros, exportaciones, actualizaciones o simulaciones.

La navegación funciona mediante elementos del menú con atributo `data-page`. Al hacer clic, el sistema activa la página correspondiente, cambia el título superior, marca el elemento del menú como activo y redimensiona las gráficas.

## 3. Paneles de navegación

### 3.1 Inicio / Panel de control

Este es el panel principal o vista ejecutiva del sistema. Resume el estado general del filtrado web.

Funciones principales:

- Muestra solicitudes totales procesadas.
- Indica sitios bloqueados.
- Presenta alertas activas.
- Muestra usuarios activos.
- Resume el estado operativo del sistema y sincronización FortiGuard.
- Incluye eventos recientes relevantes.
- Presenta gráficas de tráfico permitido y bloqueado.
- Muestra la distribución de acciones: permitidas, bloqueadas y advertencias.

Cómo funciona:

El usuario entra primero a esta vista para evaluar rápidamente la salud del filtrado web. Sirve para detectar picos de tráfico, bloqueos anormales, alertas críticas o problemas de sincronización con FortiGuard.

### 3.2 Filtrado Web

Este panel administra el motor principal de filtrado web.

Funciones principales:

- Activar o desactivar el filtrado web global.
- Controlar tráfico HTTP/HTTPS saliente.
- Habilitar filtrado por categorías FortiGuard.
- Gestionar listas URL.
- Aplicar inspección SSL.
- Forzar SafeSearch.
- Activar modo auditoría.
- Revisar perfiles de filtrado: Estándar, Estricto BYOD, IT/Admin e Invitados.

Cómo funciona:

El botón de filtrado permite cambiar entre estado activo e inactivo. Cuando se desactiva, cambia el estado visual del módulo y el botón pasa a permitir la activación. Este panel define si el entorno bloquea realmente el tráfico o solo lo registra para auditoría.

### 3.3 Usuarios y Perfiles

Este panel gestiona los usuarios, direcciones IP, perfiles asignados y actividad de navegación.

Funciones principales:

- Ver total de usuarios registrados.
- Ver usuarios conectados.
- Identificar usuarios con alertas.
- Consultar grupos configurados.
- Filtrar usuarios por búsqueda o perfil.
- Revisar tabla con usuario, IP, perfil, solicitudes y estado.
- Ver perfiles disponibles: Estándar, Estricto BYOD, Administrador, Invitados y VLAN Test.
- Analizar actividad por perfil y solicitudes por usuario.

Cómo funciona:

Permite investigar usuarios específicos por nombre, IP o perfil. También ayuda a identificar usuarios con demasiadas solicitudes, consumo elevado o estados de alerta/cuota.

### 3.4 Alertas

Este panel concentra eventos que requieren atención operativa.

Funciones principales:

- Mostrar alertas activas.
- Marcar todas como leídas.
- Bloquear host ante eventos críticos.
- Ignorar alertas.
- Ampliar cuotas cuando un grupo está por llegar al límite.
- Actualizar FortiGuard cuando hay nueva base disponible.
- Ver severidad de alertas y evolución por hora.

Cómo funciona:

Funciona como una cola de respuesta para el equipo de seguridad. Prioriza eventos como descarga de malware, cuotas casi agotadas o actualizaciones pendientes de FortiGuard.

### 3.5 Políticas

Este panel administra reglas de control de acceso web.

Funciones principales:

- Crear una nueva política.
- Revisar políticas en orden de prioridad.
- Ver alcance, usuarios afectados, acción, categorías y estado.
- Editar reglas existentes.
- Gestionar reglas como whitelist corporativa, política general, restricción BYOD, cuotas y acceso para administradores.
- Ver gráficas de hits por política y acciones configuradas.

Cómo funciona:

Las políticas se aplican en orden descendente de prioridad. Las reglas superiores tienen mayor prioridad. Sirve para definir quién puede acceder a qué contenido y bajo qué acción: permitir, bloquear, monitorear o aplicar cuota.

### 3.6 Categorías FortiGuard

Este panel permite controlar categorías de contenido clasificadas por FortiGuard.

Funciones principales:

- Gestionar 90 categorías de contenido web.
- Organizar categorías por familias: seguridad, productividad, legal/cumplimiento, aplicaciones/tecnología, noticias/educación.
- Definir acciones como bloquear, permitir, monitorear o aplicar cuota.
- Analizar categorías por acción y nivel de riesgo.

Cómo funciona:

FortiGuard clasifica cada URL según su tipo de contenido. Este panel permite decidir qué categorías deben bloquearse por seguridad, cuáles monitorear y cuáles limitar por productividad.

### 3.7 Listas URL

Este panel gestiona listas blancas y listas negras personalizadas.

Funciones principales:

- Añadir URL o patrón.
- Revisar lista blanca con dominios permitidos.
- Revisar lista negra con dominios bloqueados.
- Eliminar entradas.
- Ver quién añadió cada dominio y fecha de registro.
- Analizar crecimiento de listas y motivos de bloqueo.

Cómo funciona:

Las listas URL permiten crear excepciones específicas. La lista blanca permite dominios confiables aunque entren en categorías restrictivas. La lista negra bloquea dominios peligrosos o no permitidos aunque no estén clasificados todavía.

### 3.8 Cuotas

Este panel administra límites diarios de navegación por categoría o grupo.

Funciones principales:

- Revisar consumo de cuotas del día.
- Configurar categoría con límite diario en minutos.
- Aplicar cuota a grupos específicos.
- Guardar o cancelar cambios.
- Ver consumo por categoría.
- Detectar usuarios cerca del límite.

Cómo funciona:

Sirve para limitar el uso de categorías como redes sociales, streaming, juegos, foros o noticias. No necesariamente bloquea de inmediato, sino que permite acceso hasta alcanzar el tiempo configurado.

### 3.9 Monitoreo de Tráfico

Este panel muestra análisis del tráfico HTTP/HTTPS en tiempo real.

Funciones principales:

- Ver solicitudes por segundo.
- Medir ancho de banda consumido.
- Ver URLs únicas bloqueadas.
- Calcular tasa de bloqueo.
- Graficar tráfico web de las últimas 24 horas.
- Ver dominios más bloqueados.
- Ver páginas permitidas más visitadas.
- Revisar IPs activas y consumo de ancho de banda.
- Analizar distribución de ancho de banda.

Cómo funciona:

Ayuda a detectar consumo excesivo, anomalías, dominios sospechosos o equipos con mucho tráfico. Es útil para cruzar información con logs y políticas.

### 3.10 Logs y Reportes

Este panel conserva el historial de navegación y eventos de filtrado.

Funciones principales:

- Buscar eventos por texto.
- Filtrar por acción: bloqueado, permitido, advertencia o cuota.
- Filtrar por usuario.
- Limpiar filtros.
- Exportar eventos visibles a CSV.
- Preparar exportación PDF mediante impresión del navegador.
- Ver historial con hora, usuario/IP, URL, categoría, acción y tamaño.
- Generar reportes por fecha.
- Ver resumen de bloqueos del día.

Cómo funciona:

La tabla de logs se filtra dinámicamente. Al exportar CSV, solo se exportan las filas visibles después del filtro. El PDF usa la función de impresión del navegador para guardar la vista actual como reporte.

### 3.11 Configuración Avanzada

Este panel integra módulos de seguridad adicionales alrededor del filtrado web.

Funciones principales:

- Revisar estado del antivirus.
- Revisar IDS/IPS.
- Configurar DNS Filtering.
- Configurar alertas.
- Definir umbral de alertas de malware.
- Seleccionar canal de notificación: correo, Syslog, SNMP Trap o Webhook.
- Definir correo de alertas.
- Probar alertas.
- Aplicar cambios.
- Ver estado de módulos UTM y eventos por motor.

Cómo funciona:

Extiende el filtrado web con defensa profunda. Permite controlar inspección antivirus, prevención de intrusiones, filtrado DNS y notificaciones automáticas ante eventos importantes.

### 3.12 FortiGuard DB

Este panel muestra el estado del servicio de inteligencia de amenazas FortiGuard.

Funciones principales:

- Ver versión actual de la base.
- Ver categorías activas.
- Ver URLs en caché.
- Validar días restantes de licencia.
- Actualizar la base FortiGuard.
- Revisar servidor FortiGuard.
- Configurar inspección.
- Ver sincronización y cobertura de base de datos.

Cómo funciona:

FortiGuard proporciona clasificación de URLs, reputación y firmas de amenazas. Este panel valida que la base esté actualizada y que la licencia continúe vigente.

### 3.13 Ajustes

Este panel administra parámetros generales del sistema.

Funciones principales:

- Ver información del dispositivo.
- Consultar modelo FortiGate 200F.
- Consultar versión FortiOS.
- Ver datos operativos del sistema.
- Configurar notificaciones y alertas.
- Guardar ajustes.
- Ver uso de recursos del dispositivo.
- Revisar histórico de uptime.

Cómo funciona:

Centraliza información administrativa del equipo y ajustes de notificación. Es útil para documentación, soporte y mantenimiento operativo.

### 3.14 Ayuda

Este panel funciona como guía de uso y documentación interna.

Funciones principales:

- Explicar qué es el filtrado web.
- Describir cómo funciona FortiGate.
- Resumir módulos del sistema.
- Mostrar buenas prácticas.
- Presentar recomendaciones operativas.
- Graficar uso recomendado por módulo y madurez operativa.

Cómo funciona:

Sirve como apoyo para usuarios técnicos o administradores nuevos. Resume el flujo básico: el usuario solicita una web, FortiGate intercepta el tráfico, consulta FortiGuard, aplica políticas y permite, bloquea o registra la solicitud.

## 4. Funciones transversales del dashboard

### Buscador global

Permite escribir palabras clave como logs, usuario, tráfico, política, categoría, cuota, FortiGuard, ajuste o ayuda. Al presionar Enter, abre automáticamente el módulo relacionado.

### Botón de actualización

Actualiza métricas simuladas, cambia el valor de bloqueos por minuto y marca la sincronización FortiGuard como reciente.

### Acceso rápido a logs

El botón superior de logs abre directamente el panel Logs y Reportes.

### Menú colapsable

El botón de menú permite colapsar o expandir la barra lateral para ganar espacio visual.

### Gráficas

El dashboard usa Chart.js para presentar datos en gráficos de barras, líneas, dona, radar y polar. Cada módulo tiene visualizaciones propias para apoyar la interpretación de datos.

### Exportaciones

El panel Logs y Reportes permite exportar CSV con los eventos filtrados y preparar PDF mediante la impresión del navegador.

### Reproductor de música

Incluye un reproductor flotante con controles de reproducir, pausar, detener y volumen. Su posición se puede mover y se guarda en el navegador.

## 5. Conclusión

El Dashboard FortiGate Web es una interfaz integral para administrar el filtrado web corporativo. Permite supervisar tráfico, aplicar políticas, controlar usuarios, clasificar contenido, administrar excepciones URL, limitar tiempos de navegación, responder alertas, revisar logs, generar reportes y validar el estado de FortiGuard.

Su valor principal está en centralizar la operación de seguridad web en un solo entorno visual, facilitando la toma de decisiones rápidas para protección, productividad y cumplimiento.
