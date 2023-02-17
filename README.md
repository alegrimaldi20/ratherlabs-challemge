# Challenge de RatherLabs

Para este desafío decidí usar la api de bitfinex a través de websocket, bitfinex tiene una mejor experiencia para desarrolladores y mejor documentación.

## Stack
- Nodejs
- Express
- Configuracion: dotenv
- Jest: Para Test

## Arquitectura

El proyecto se divide en varias capas, cada una con diferentes responsabilidades. Tres se destacan consumidor / memoria / servidor api .

- Comsumer: Obtener los datos del socket y mantener el libro actualizado en memoria, separados por compra y venta.
- Api: Interfaz HTTP para obtener las diferentes funcionalidades propuestas.
- Configuración : Aquí centralizo la configuración de donde obtuvo información la api o el consumidor

## Comandos

Estos son varios comandos para ejecutar el proyecto.

### Ejecutar test:

``npm test``

### Ejecutar informe de coverage

``npm run coverage``
### Ejecute la aplicación en modo de desarrollo

``npm run dev``

## Final Points

Ejemplos de cómo usar los final points:

### Pregunta de oferta
Reciba un pair name y recupere los precios de oferta y demanda
```http://127.0.0.1:2000/orders/tBTCUSD/prices```
```http://127.0.0.1:2000/orders/tETHUSD/prices```

### Simular la ejecución de una orden

Reciba un par, nombre una operación, monto y devuelva el precio si se ejecuta la orden ```http://127.0.0.1:2000/market/execute/:pair-name/[BUY/SELL]/:ammount```

Ejemplo : ```http://127.0.0.1:2000/market/execute/tBTCUSD/BUY/2```
```http://127.0.0.1:2000/market/execute/tBTCUSD/SELL/2```

### Simular la ejecución de órdenes con limit bonus

Reciba un par, nombre una operación, límite, monto y devuelva el precio si se ejecuta la orden: ```http://127.0.0.1:2000/market/execute/:pair-name/[BUY/SELL]/:ammount/limit/:limit-ammount```

Ejemplo:
```http://127.0.0.1:2000/market/execute/tBTCUSD/BUY/2/limit/50```
```http://127.0.0.1:2000/market/execute/tBTCUSD/SELL/2/limit/500```


Nota: Los pares comerciales están precedidos por una "t" antes del par (por ejemplo: tBTCUSD y tETHUSD) el proyecto solo funciona con pares comerciales compatibles con bitfinex. https://docs.bitfinex.com/docs/ws-general
