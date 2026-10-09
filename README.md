## Olá, curioso(a)! <img src="https://cdn.discordapp.com/emojis/1184599007629152336.gif?size=80&quality=lossless" width="40">
<p style="font-size:14px;">
```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Auto Center Veloz</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>

    <aside class="sidebar">
        <div class="brand">
            <div class="brand-mark">AV</div>
            <div>
                <strong>Auto Center</strong>
                <span>VELOZ</span>
            </div>
        </div>

        <div class="side-label">MENU PRINCIPAL</div>

        <button class="nav-item active" data-view="dashboard">
            Visão geral
        </button>

        <button class="nav-item" data-view="vehicles">
            Veículos
        </button>

        <button class="nav-item" data-view="budgets">
            Orçamentos
            <b class="nav-count" id="pendingNav">2</b>
        </button>
    </aside>

    <main class="main">

        <header class="topbar">
            <div class="breadcrumb">
                Oficina / <strong id="crumb">Visão geral</strong>
            </div>
        </header>

        <section class="page" id="dashboardView">

            <div class="page-heading">
                <div>
                    <p class="eyebrow">PAINEL DA OFICINA</p>
                    <h1>Visão geral</h1>
                </div>

                <button class="primary-btn" id="newVehicleBtn">
                    + Cadastrar veículo
                </button>
            </div>

            <div class="stats-grid">

                <article class="stat-card">
                    <div class="stat-top">
                        <span>Veículos na oficina</span>
                    </div>
                    <strong id="statVehicles">6</strong>
                </article>

                <article class="stat-card">
                    <div class="stat-top">
                        <span>Orçamentos pendentes</span>
                    </div>
                    <strong id="statPending">2</strong>
                </article>

                <article class="stat-card">
                    <div class="stat-top">
                        <span>Em manutenção</span>
                    </div>
                    <strong id="statProgress">3</strong>
                </article>

                <article class="stat-card">
                    <div class="stat-top">
                        <span>Prontos para retirada</span>
                    </div>
                    <strong id="statReady">1</strong>
                </article>

            </div>

            <div class="content-grid">

                <section class="panel vehicles-panel">

                    <div class="panel-heading">
                        <h2>Veículos recentes</h2>

                        <button class="text-btn" data-go="vehicles">
                            Ver todos
                        </button>
                    </div>

                    <div class="table-wrap">
                        <table>
                            <thead>
                                <tr>
                                    <th>VEÍCULO / CLIENTE</th>
                                    <th>SERVIÇO</th>
                                    <th>STATUS</th>
                                    <th>PREVISÃO</th>
                                    <th></th>
                                </tr>
                            </thead>

                            <tbody id="vehicleRows"></tbody>
                        </table>
                    </div>

                </section>

                <section class="panel approvals-panel">

                    <div class="panel-heading">
                        <h2>Orçamentos pendentes</h2>
                        <span class="counter" id="pendingCount">
                            2 pendentes
                        </span>
                    </div>

                    <div id="approvalList" class="approval-list"></div>

                </section>

            </div>

            <section class="panel workflow-panel">

                <div class="panel-heading">
                    <h2>Fluxo de atendimento</h2>
                </div>

                <div class="workflow">

                    <div class="flow-step">
                        <div class="flow-number">1</div>
                        <strong>Entrada</strong>
                        <span>Cadastro</span>
                    </div>

                    <div class="flow-line"></div>

                    <div class="flow-step">
                        <div class="flow-number">2</div>
                        <strong>Orçamento</strong>
                        <span>Aprovação</span>
                    </div>

                    <div class="flow-line"></div>

                    <div class="flow-step">
                        <div class="flow-number">3</div>
                        <strong>Manutenção</strong>
                        <span>Execução</span>
                    </div>

                    <div class="flow-line"></div>

                    <div class="flow-step">
                        <div class="flow-number">4</div>
                        <strong>Retirada</strong>
                        <span>Entrega</span>
                    </div>

                </div>
            </section>

        </section>

        <section class="page hidden" id="vehiclesView">

            <div class="page-heading">
                <div>
                    <p class="eyebrow">VEÍCULOS</p>
                    <h1>Veículos cadastrados</h1>
                </div>

                <button class="primary-btn" id="newVehicleBtn2">
                    + Cadastrar veículo
                </button>
            </div>

            <section class="panel">

                <div class="table-wrap">
                    <table>
                        <thead>
                            <tr>
                                <th>VEÍCULO / CLIENTE</th>
                                <th>SERVIÇO</th>
                                <th>STATUS</th>
                                <th>PREVISÃO</th>
                                <th></th>
                            </tr>
                        </thead>

                        <tbody id="vehicleRows2"></tbody>
                    </table>
                </div>

            </section>

        </section>

        <section class="page hidden" id="budgetsView">

            <div class="page-heading">
                <div>
                    <p class="eyebrow">ORÇAMENTOS</p>
                    <h1>Orçamentos</h1>
                </div>
            </div>

            <section class="panel">
                <div id="budgetPageList" class="budget-page-list"></div>
            </section>

        </section>

    </main>

    <dialog id="vehicleDialog">

        <form id="vehicleForm" method="dialog">

            <div class="dialog-head">
                <h2>Cadastrar veículo</h2>

                <button type="button" class="close-btn" id="closeDialog">
                    ×
                </button>
            </div>

            <div class="form-grid">

                <label>
                    Nome do cliente
                    <input name="client" required>
                </label>

                <label>
                    Telefone
                    <input name="phone" placeholder="(41) 99999-9999">
                </label>

                <label>
                    Modelo do veículo
                    <input name="model" required>
                </label>

                <label>
                    Placa
                    <input name="plate" maxlength="8" required>
                </label>

                <label class="full">
                    Serviço solicitado
                    <input name="service" required>
                </label>

                <label>
                    Status
                    <select name="status">
                        <option>Em manutenção</option>
                        <option>Aguardando aprovação</option>
                        <option>Aguardando peças</option>
                        <option>Pronto para retirada</option>
                    </select>
                </label>

                <label>
                    Previsão de entrega
                    <input name="due" placeholder="Ex.: Hoje, 16:00">
                </label>

            </div>

            <div class="dialog-actions">
                <button type="button" class="secondary-btn" id="cancelDialog">
                    Cancelar
                </button>

                <button class="primary-btn" type="submit">
                    Salvar veículo
                </button>
            </div>

        </form>

    </dialog>

    <div id="toast" class="toast" role="status"></div>

    <script src="script.js"></script>

</body>
</html>
```
