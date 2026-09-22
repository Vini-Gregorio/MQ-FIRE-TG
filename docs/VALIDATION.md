# Evidência da refatoração — 22/09/2026

Este registro descreve verificações executadas, não certificação nem resultado de ensaio físico. A importação foi validada no próprio `MQ-FIRE-TG`: [execução 35707757501](https://github.com/Vini-Gregorio/MQ-FIRE-TG/actions/runs/35707757501), commit **`a7f09b55f0957824cc6bdc9c7de6e9555d1cd43b`**, jobs **software** e **firmware** concluídos com sucesso em 22/09/2026. A árvore publicada foi comparada à cópia preparada e corresponde integralmente aos 64 arquivos revisados.

A [CI da revisão de origem, commit c9a9bb2](https://github.com/Vini-Gregorio/SensorFumaca/actions/runs/35681701365), fica como referência histórica. Para qualquer revisão posterior, conferir SHA e conclusão na [CI do MQ-FIRE-TG](https://github.com/Vini-Gregorio/MQ-FIRE-TG/actions/workflows/ci.yml); aprovação de um commit não se estende automaticamente ao seguinte.

| Verificação | Resultado observado nesta execução |
|---|---|
| `npm test` | 26 testes aprovados localmente e na CI do commit a7f09b5, 0 falhas, 0 pulados; inclui contrato experimental, proteção das novas rotas e conclusão explícita |
| `npm run test:firmware` | Núcleo C++11 compilado com `-Wall -Wextra -Werror`; assertions de alarme, debounce, rollover, canais independentes, prioridade, substituição e transbordamento da fila aprovadas |
| `npm run check:secrets` | Árvore atual aprovada pelo verificador básico; não verifica histórico |
| `npm audit --omit=dev` | 0 vulnerabilidades conhecidas nos logs da CI da importação; resultado pontual do registro npm |
| `git diff --check` | Sem erros de whitespace na verificação local |
| `npm run test:integration` local | Não executado com banco: Docker/MariaDB não disponíveis; tentativa de instalação bloqueada por permissões. Sem flag, teste explicitamente pulado |
| Integração MariaDB na CI | Aprovada no MQ-FIRE-TG: 3 testes, 0 falhas e 0 pulados. Upgrade 001 → 002 → 003 e repetição das migrações aprovados, incluindo ensaios, isolamento, limites e exportação conjunta |
| Smoke Chromium | Aprovado no MQ-FIRE-TG: planejar/iniciar/anotar/concluir/exportar ensaio, autenticação/XSS/mobile/desktop e limpeza dos dados ao sair |
| Compilação ESP32 PlatformIO | Aprovada no MQ-FIRE-TG com toolchain C++11; fila e diagnóstico compilados. Sem credenciais reais e sem gravação em hardware |
| Carga k6 / hardware / Telegram real / campo | Não executados |
| Revogação de segredos externos / limpeza do histórico | Não executadas; requerem responsável e coordenação |
| Repositório independente | `Vini-Gregorio/MQ-FIRE-TG` público, criado em 22/09/2026; API confirmou `fork: false`. Arquivos revisados importados sem histórico antigo; créditos preservados. O fork anterior permanece intacto |

## Cobertura e limites

- Testes HTTP usam dublê do repositório SQL: validam contrato, autenticação, origem, limites e respostas de falha, não transações reais.
- Integração separada exercita MariaDB real. O teste de upgrade recusa banco não vazio e confirma snapshot dos limites existentes sem fabricar versões passadas. Uma falha injetada depois de editar limites verifica rollback de valores e versão; uma resposta de worker com reserva antiga deve ser ignorada.
- Smoke do navegador usa banco simulado e exercita UI/HTTP real. Não equivale a ponta a ponta com hardware/DB.
- Teste embarcado nativo verifica lógica pura e a política de fila; compilação PlatformIO verifica toolchain/headers. Nenhum deles comprova agendamento das tarefas, pinagem, temporização física, estabilidade elétrica ou comportamento do MQ-2.
- Auditoria de dependências é uma fotografia; manter atualização e reexecutar antes do deploy.
- Não houve acesso ao ambiente Render, mudança no banco de produção, atualização do documento do Drive nem criação de repositório comercial.

Antes de integrar/deployar: revisar código, executar CI, reproduzir instalação limpa e ensaio físico com protocolo aprovado. Usar docs/TG-ROADMAP.md para registrar evidências e resolver as lacunas.
