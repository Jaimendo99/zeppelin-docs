# Live Session Events

Estos son eventos que ocurren al momento de una sesion activa de trabajo.
Aquí se envin eventos que son relevantes para alguno de los dispositivos conectados por ejemplo: se empieza la sesion pomodoro.

## Eventos

- **`status_update`**: Actualiza el número de conexiones y plataformas conectadas.
  ```json
  {
    "type": "status_update",
    "connections": "number",
    "platforms": {
      "web": "number",
      "mobile": "number"
    }
  }
  ```

### Pomodoro control

- **`pomodoro_start`**: Inicia el Pomodoro con la configuración dada.
  ```json
  {
    "type": "pomodoro_start",
    "started_at": 10,
    "sessionId": "string",
    "senderId": "string",
    "config": {
      "workDuration": 10,
      "breakDuration": 3,
      "cycles": 3
    }
  }
  ```
- **`pomodoro_extend`**: Extiende el temporizador actual por 2 segundos.
  ```json
  {
    "type": "pomodoro_extend",
    "seconds": 2,
    "sessionId": "string",
    "senderId": "string"
  }
  ```
- **`pomodoro_phase_end`**: "break", nextCycle: number, isBreakFinished: boolean, isLastCycle: boolean, continueAs: "work"
  ```json
  {
    "type": "pomodoro_phase_end",
    "sessionId": "string",
    "phase": "work"
  }
  ```
- **`pomodoro_session_end`**: Finaliza la sesión Pomodoro tras completar todos los ciclos.
  ```json
  {
    "type": "pomodoro_session_end",
    "sessionId": "string",
    "senderId": "string"
  }
  ```

### DISTRACTION EVENT

#### WEARABLE APP

- **`WEARABLE_OFF`**: cuando el usuario se quita el wearable mientras en sesion de trabajo.
  ```json
  {
    "type": "WEARABLE_OFF",
    "time": "timestamp"
  }
  ```
  - Trigger WebApp -> Pomodoro off State
- **`WEAK_RSSI`**: cuando el wearable tiene una señal muy baja lo que determinaría una distancia lejana.
  ```json
  {
    "type": "WEAK_RSSI",
    "rssi": "decibeles"
  }
  ```
  - Trigger WebApp -> Pomodoro off State
- **`WEARABLE_DISCONNECTED`**: cuando el wearable se desconecta del dispositivo android.
  ```json
  {
    "type": "WEARABLE_DISCONNECTED",
    "time": "timestamp"
  }
  ```
  - Trigger WebApp -> Pomodoro off State

#### MOBILE APP

- **`UNPIN_SCREEN`**: cuando el usuario le quita el bloqueo de pantalla de zeppelin.
  ```json
  {
    "type": "UNPIN_SCREEN",
    "removed_at": "timestamp"
  }
  ```
  - Trigger WebApp -> Pomodoro off State
