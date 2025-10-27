# Como Funciona

Fluxo principal:

1. **Configuração de Fila**: Admin/Staff define nome, vigência, permissões, limites e mensagens.
2. O sistema gera **TOKEN_FILA**, **URL pública** e **QR Code**.
3. Clientes entram pela **página pública** (validações de vigência, bloqueio do dia e duplicidade por CPF).
4. **Gestão da Fila (Dia)**: equipe chama/gerencia clientes em tempo real.
5. **Painel Público (TV)**: exibe chamados e ordem.
6. **Dashboard**: KPIs e gráficos com atualização contínua.

!!! tip "Bloquear novas entradas hoje"
    Use o bloqueio na **fila do dia** (não na configuração) para impedir **entradas públicas** sem impactar a gestão de quem já está aguardando.
