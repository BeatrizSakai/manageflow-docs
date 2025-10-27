# Dashboard (Tempo real)

## KPIs
- Configurações de fila (total / ativas)
- Filas bloqueadas hoje
- Pessoas hoje
- Tempo médio de espera atual
- Aguardando por fila

## Atualização dos dados
- **WebSocket** dispara `dashboard:tick` a cada ~10s para re-fetch.
- Eventos como `cliente_atualizado` forçam atualização imediata.

## Gráficos
- Entradas por hora (agregação por hora no banco)
- Tendência diária e comparativos
