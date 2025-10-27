# Módulos da Aplicação

## 1) Autenticação & Empresas
- **Login/Cadastro** via JWT.
- **Empresa**: dados gerais, imagens (banner/logo) e preferências.
- **Associação de usuários** à empresa com papéis (Admin/Staff/Analyst).

## 2) Configuração de Fila
- Campos: **NOME_FILA**, **INI_VIG/FIM_VIG** (vigência), **permissões** (ex.: per_sair, per_loc), **tolerância**, **limites**, **mensagens**.
- Uploads: `img_banner`, `img_logo` (armazenar **caminho relativo** `/uploads/...` e expor **URL pública** na resposta).
- Gera **TOKEN_FILA**, **URL pública** e **QR Code**.
- **Ativa de fato** quando `SITUACAO = 1` **e** a data atual está dentro da vigência.

## 3) Gestão de Fila (Diária)
- A **fila do dia** nasce a partir da configuração quando o primeiro cliente entra (ou criada pela equipe).
- Campos-chave na tabela do dia: **`BLOCK`** (bloqueio de entradas hoje) e **`SITUACAO`** (ativa/inativa hoje).
- Ações: **chamar**, **confirmar presença**, **não compareceu**, **remover**, **atendido**.
- Bloqueio: `PUT /filas/:id_fila/block { block: boolean }` → `BLOCK=1` (e opcionalmente `SITUACAO=0`).

## 4) Fluxo Público (Entrada na Fila)
- Acesso por **TOKEN_FILA** (URL pública / QR Code).
- Validações: **configuração ativa + vigente**, **fila do dia não bloqueada/ativa**, **sem duplicidade por CPF no mesmo dia**.
- Feedback ao cliente: posição, status e mensagens da casa.

## 5) Painel Público (TV)
- Exibe ordem/chamados em **tempo real** (WebSockets).
- Layout pensado para monitores/TVs no salão.

## 6) Dashboard & Relatórios
- KPIs: configurações (total/ativas), **bloqueadas hoje**, **pessoas hoje**, **tempo médio de espera atual**, **aguardando por fila**.
- Gráficos: **entradas por hora** (ex.: `DATE_FORMAT(DT_ENTRA, '%Y-%m-%d %H:00:00')` no GROUP BY).
- Atualização: **WebSocket “tick”** e **re-fetch a cada ~10s**.
- Exportáveis: CSV/Excel/PDF.
