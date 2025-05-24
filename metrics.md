# Métricas monitoreo distracción

## Web App

### Eventos comunes

- **`CONTENT_COMPLETED`**: métrica de finalización de contendio. Se envía al terminar cada contendio:

  ```json
  "body": {
    "start_time": "timestamp",
    "start_end": "timestamp"
  }
  ```

- **`TAB_FOCUS_LOST`**: el usuario ingresa a otra ventana/tab o aplicacion lo que resulta en una perdida del enfoque en la app de zeppelin, mientras esta en una sesion activa.
  ```json
  {}
  ```
- **`TAB_FOCUS_GAIN`**: el usuario vuelve a enfocarse en la ventana de contenido zeppelin.
  ```json
  {}
  ```

### Contenido de texto:

- **`TEXT_SCROLL`**: esta métrica se captura en cada evento de scroll. Un evento de scroll es cada vez que se empiza un scroll hasta que se detiene el moviento.
  ```json
  {
    "body": {
      "current_scroll_position": "int",
      "scroll_direction": "down/up",
      "scroll_distance": "int",
      "scroll_porcentage": "int"
    }
  }
  ```

### Contenido de video:

- **`VIDEO_PAUSED`**: el tiempo desde que se pausó el video hasta que se reproduzca de nuevo.
- **`VIDEO_JUMP`**: cuando el usuario adelanta o atrasa el video:
  ```json
  "body": {
      "jump_to":"seconds", // el segundo del video al que se saltó
      "direction":"forward/backward"
  }
  ```
- **`VIDEO_SPEED_CHANGED`**: el usuario cambia la velocidad del video.
  ```json
  "body": {
      "speed": "float"
  }
  ```
- **`VIDEO_PERCENTAGE`**: el porcentaje de vista del video en el contenido.
  ```json
  "body": {
      "percentage": "float" // 0-1
  }
  ```

### Contenido de quiz:

- **`QUESTION_DURATION`**: el tiempo que el usuario/estudiante se demora en cada pregunta.
  ```json
  "body":{
      "question_id":"stringid",
      "time_spent_on_question":"int[seconds]"
  }
  ```

## MOBILE APP

- **`UNPIN_SCREEN`**: cuando el usuario le quita el bloqueo de pantalla de zeppelin.
  ```json
  "body":{
      "removed_at":"timestamp"
  }
  ```
- **`APP_USAGE`**: un reporte de uso de aplicaciones de redes sociales y juegos en un determinado tiempo. En cada desconexion de websocket.
  ```json
  "body":{
      "usage": [
         {
           "packageName": "String",
           "totalTimeInForeground": "Long", // long : timestamp
           "usageIntervalStart": "Long",
           "usageIntervalEnd": "Long",
           "lastTimeAppUsed": "Long"
           }
      ],
  }
  ```

## WEARABLE APP

- **`USER_HEARTRATE`**: el cambio de ritmo cardiaco a lo largo de la sesion.
  ```json
  "body":{
      "heartrate_change":[
          {
              "value":120,
              "time":"timestamp"
          }
      ],
  }
  ```
- **`USER_PHYSICAL_ACTIVITY`**: reporte de actividad fisica significativa o llamativa en momento de concentracion, por ejemplo: caminar, saltar, o otras actividades fisicas.

  ```json
  "body": {}
  ```

- **`WEARABLE_OFF`**: cuando el usuario se quita el wearable mientras en sesion de trabajo.
  ```json
  "body":{
    "time":"timestamp"
  }
  ```
- **`WEAK_RSSI`**: cuando el wearable tiene una señal muy baja lo que determinaría una distancia lejana.
  ```json
  "body":{
    "rssi":"decibeles"
    }
  ```
- **`WEARABLE_DISCONNECTED`**: cuando el wearable se desconecta del dispositivo android.
  ```json
  "body":{
    "time":"timestamp"
  }
  ```
