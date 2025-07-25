# Challenge Técnico: Sistema de Reservas Médicas

## Información General

**Tiempo estimado:** 2-3 días  
**Enfoque:** Funcionalidad básica antes que detalles visuales  
**Uso de IA:** Obligatorio (documenta tu proceso)

## Instrucciones de Entrega

### Repositorio:
1. **Crear repositorio privado** en GitHub o GitLab
2. **Agregar como colaborador** a: [TU_EMAIL_O_USERNAME]
3. **Enviar link del repositorio** por email cuando esté completo

---

## Contexto del Proyecto

Una clínica médica necesita un sistema básico para que los pacientes puedan agendar citas online. Actualmente todo se maneja por teléfono y quieren digitalizar el proceso para mejorar la eficiencia y experiencia del paciente.

---

## Requerimientos Funcionales

### Como Paciente quiero:
- Ver horarios disponibles para una fecha específica
- Reservar una cita proporcionando mis datos básicos
- Ver confirmación de mi reserva con todos los detalles
- Poder cancelar mi cita si es necesario

### Como Administrador quiero:
- Ver todas las citas programadas para un día específico
- Poder cancelar citas en caso de emergencias o reprogramaciones
- Tener una vista clara del estado de la agenda

---

## Especificaciones Técnicas

### Backend (API REST)

#### Endpoints requeridos:

```
POST /api/appointments
- Crear nueva cita
- Body: { 
    patientName: string,
    email: string,
    phone: string,
    date: string (YYYY-MM-DD),
    time: string (HH:MM),
    reason: string (opcional)
  }
- Response: { id, appointmentCode, ...appointmentData }

GET /api/appointments/available?date=2025-07-25
- Obtener horarios disponibles para una fecha específica
- Response: { availableSlots: ["09:00", "09:30", "10:00", ...] }

GET /api/appointments?date=2025-07-25
- Listar todas las citas para una fecha (uso administrativo)
- Response: { appointments: [...] }

DELETE /api/appointments/:id
- Cancelar cita específica
- Response: { success: boolean, message: string }
```

### Frontend

#### Pantallas principales:
1. **Formulario de reserva** - Selección de fecha, horario y datos del paciente
2. **Confirmación** - Mostrar detalles de la cita creada
3. **Panel administrativo** - Lista de citas del día
4. **Vista responsive** - Funcional en dispositivos móviles

---

## Reglas de Negocio

### Horarios y Disponibilidad:
- **Horario de atención:** 9:00 a 17:00, lunes a viernes
- **Duración por cita:** 30 minutos
- **Horarios disponibles:** 09:00, 09:30, 10:00, 10:30, ... 16:30

### Restricciones:
- No se pueden agendar citas para fechas pasadas
- No se pueden agendar citas con menos de 24 horas de anticipación
- Máximo una cita por email por día
- Validar formato de email y teléfono

### Datos requeridos:
- **Obligatorios:** Nombre completo, email, teléfono, fecha, hora
- **Opcionales:** Edad, motivo de consulta

---

## Stack Tecnológico Requerido

### Backend:
- **Node.js** con Express
- Estructura RESTful con rutas claras
- Manejo de JSON para requests/responses

### Frontend:
- **Next.js** (React framework)
- Componentes funcionales con hooks

### Base de Datos:
- **Archivos JSON locales** para persistir datos
- Lectura/escritura síncrona con `fs`

---

## Entregables

### 1. Repositorio de Código
- **Crear un repositorio privado** en GitHub o GitLab
- **Compartir acceso** al repositorio con el evaluador
- Incluir todo el código fuente del proyecto
- **Commits frecuentes** que muestren el progreso del desarrollo

### 2. README Completo
Debe incluir:
- **Cómo ejecutar el proyecto** (paso a paso)
- **Decisiones de diseño** tomadas durante el desarrollo
- **Limitaciones conocidas** o funcionalidades faltantes
- **Proceso de desarrollo** (documentación del uso de IA)

---

## Criterios de Evaluación

### Funcionalidad (40%)
- ¿Cumple los requerimientos básicos?
- ¿Las reglas de negocio están implementadas?
- ¿La aplicación funciona sin errores críticos?

### Calidad del Código (30%)
- ¿Es legible y está bien organizado?
- ¿Hay separación clara de responsabilidades?
- ¿El código es mantenible?

### Experiencia de Usuario (20%)
- ¿Es intuitivo usar la aplicación?
- ¿Los mensajes de error son claros?
- ¿Funciona bien en dispositivos móviles?

### Documentación (10%)
- ¿Puedo ejecutar el proyecto siguiendo las instrucciones?
- ¿Explicas bien tus decisiones?
- ¿Es clara la documentación del uso de IA?
- ¿Los commits muestran un desarrollo progresivo?

---

## Nota Importante sobre IA

**Debes usar herramientas de IA** para ayudarte en el desarrollo. Preferentemente:

### Herramientas Recomendadas:
1. **Gemini CLI** (Google) - Para consultas de código y arquitectura
2. **Cursor** - Editor con IA integrada para desarrollo
3. **GitHub Copilot** - Autocompletado inteligente

### Documentación Requerida:
En el README **debes incluir una sección** explicando tu uso de IA:

#### Ejemplo de documentación:
```markdown
## Uso de IA en el desarrollo

### Herramientas utilizadas:
- Gemini CLI para consultas sobre estructura del proyecto
- Cursor para autocompletado de componentes React
- Copilot para funciones de validación

### Consultas principales:
1. "Cómo estructurar una API REST en Express para reservas"
2. "Mejores prácticas para manejar estado en Next.js"
3. "Validación de formularios en React con hooks"

### Código generado vs propio:
- 60% generado con IA y modificado
- 40% implementado desde cero
- Toda la lógica de negocio revisada manualmente
```

### Evaluaremos:
- **Criterio técnico** en el uso de las herramientas
- **Capacidad de adaptación** del código generado
- **Comprensión** de lo que implementaste
- **Decisiones propias** vs sugerencias de IA

---

## Casos de Prueba Sugeridos

### Escenarios Happy Path:
1. Agendar cita con todos los datos correctos
2. Ver horarios disponibles para fecha válida
3. Cancelar cita existente
4. Ver lista de citas como administrador

### Casos Edge:
1. Intentar agendar para fecha pasada
2. Seleccionar horario ya ocupado
3. Agendar segunda cita el mismo día con mismo email
4. Enviar datos inválidos (email mal formato, etc.)

---

## Preguntas Frecuentes

**¿Puedo usar librerías externas?**  
Sí, pero justifica su uso en el README. Para Next.js es común usar date-fns, react-hook-form, etc.

**¿Necesito implementar autenticación?**  
No, para este challenge enfócate en la funcionalidad core.

**¿Qué pasa si no termino todas las funcionalidades?**  
Prioriza: crear cita → ver horarios → listar citas → cancelar cita.

**¿Cómo manejo los archivos JSON?**  
Usa `fs.readFileSync` y `fs.writeFileSync` en el backend. La estructura de datos queda a tu criterio.

---

## Contacto

Si tienes dudas sobre el challenge, no dudes en contactarme. **Queremos ver cómo piensas y resuelves problemas, no que seas perfecto.**

¡Éxito con el challenge! 🚀
