# Repositório independente e proveniência

## Transição em 22/09/2026

O repositório público **[Vini-Gregorio/MQ-FIRE-TG](https://github.com/Vini-Gregorio/MQ-FIRE-TG)** foi criado pela opção de novo repositório do GitHub, com `main` como branch principal. A API confirmou `fork: false`. A condução atual é de Vinícius Gregório; o escopo é acadêmico e reproduzível.

Foi importada uma cópia dos arquivos versionados de `Vini-Gregorio/SensorFumaca`, branch `refactor/tg-secure-foundation`, commit **`c9a9bb21cbe9ef083af7a6b8a7e3a01bd18f5dc6`**. Depois da cópia, a documentação e as URLs foram adaptadas ao novo destino. O registro legível por máquina está em [provenance.json](provenance.json).

- O snapshot inclui API, dashboard, migrações, firmware C++, testes e documentação da versão revisada.
- Não foram importados commits/branches/tags do legado, `.git`, `.env`, `secrets.h`, banco, dados de ensaio ou dependências instaladas.
- A árvore foi exportada com `git archive`; não foi usado Fork, mirror nem merge do histórico anterior.
- [AUTHORS.md](../AUTHORS.md) preserva os créditos de origem. Eles não indicam manutenção atual nem endosso das novas versões.
- A licença continua pendente; não foi concedida uma licença presumida.

O repositório anterior, [PR #7](https://github.com/Vini-Gregorio/SensorFumaca/pull/7) e suas evidências de CI permanecem disponíveis. O fork antigo não foi arquivado, excluído ou desvinculado. A independência se refere a este **novo repositório**.

## Evidência de partida e validação atual

A [CI da revisão de origem](https://github.com/Vini-Gregorio/SensorFumaca/actions/runs/35681701365) aprovou software e compilação ESP32. Isso é evidência da versão anterior à importação. Consulte as [execuções do novo repositório](https://github.com/Vini-Gregorio/MQ-FIRE-TG/actions/workflows/ci.yml) e [VALIDATION.md](VALIDATION.md) para verificar a versão atual. Não presumir que aprovação de um commit se estende ao seguinte.

O novo histórico começa com o README inicial criado pelo GitHub e segue com a importação documentada. Referenciar o SHA antigo como texto não o torna ancestral do novo histórico. Não enviar branches antigas nem usar `git push --mirror` neste destino.

## Segurança durante a transição

A ausência do histórico antigo aqui **não revoga credenciais que já foram expostas**. O responsável ainda precisa revogar/regenerar valores nos provedores e reconfigurar instalações, sem reutilizar configurações antigas. [SECURITY.md](../SECURITY.md) descreve essa pendência e os controles da nova aplicação.

Uma eventual exclusão, reescrita ou mudança no fork anterior é decisão separada. Preservar referências acadêmicas e combinar o tratamento de cópias afetadas antes de alterar o legado.

## Exportar uma versão para reprodução

Em um checkout limpo do novo repositório:

```sh
npm run check:secrets
npm run export:standalone -- ../mqfire-tg-source.tar
```

O TAR contém apenas arquivos versionados do commit escolhido; o manifesto separado registra SHA e hash do arquivo. O comando recusa destinos existentes e não transporta histórico ou configuração local. O verificador de segredos é básico e não substitui revisão antes da publicação.

## Próximas entregas

As prioridades e os critérios de aceite estão em [EVOLUTION.md](EVOLUTION.md): revogação e reprodução da instalação; bancada com múltiplos dispositivos/canais; ligação dos resultados ao relatório do TG. A pesquisa de IA permanece consultiva e depende de dados independentes e comparação com uma baseline.
