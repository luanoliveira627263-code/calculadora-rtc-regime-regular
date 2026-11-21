---
name: calculadora-rtc-regime-regular
description: Use ao calcular CBS, IBS ou Imposto Seletivo (Reforma Tributária, LC 214/2025) no regime geral/regular com a API da Calculadora de Tributos da Receita Federal; ao calcular base de cálculo unificada de NF-e/NFC-e/NFS-e; gerar ou validar XML contra XSD; ou consultar CST, cClassTrib, fundamentações legais, NCM, NBS e alíquotas de referência (União, UF, município).
---
# Calculadora de Tributos - Regime Regular

## Visão geral

A Calculadora de Tributos do Regime Geral é uma API REST aberta da Receita
Federal do Brasil que realiza o cálculo da **CBS**, do **IBS** e do **Imposto
Seletivo** (Reforma Tributária do Consumo — LC 214/2025) nas operações do regime
geral, consulta as tabelas oficiais usadas no cálculo e gera e valida os grupos
de tributação dos documentos fiscais eletrônicos.

## Quando usar esta skill

Use esta skill quando precisar:

- Calcular tributos do regime geral (a operação inteira falha no primeiro erro).
- Calcular com observabilidade (erros por item, sem interromper os demais).
- Consultar códigos de erro da observabilidade (`REG-`).
- Calcular a base de cálculo unificada da NF-e/NFC-e e da NFS-e.
- Gerar XML a partir do resultado do cálculo.
- Validar XML (grupo ou nota) contra o XSD.
- Consultar CST e classificações tributárias (`cClassTrib`).
- Consultar fundamentações legais, NCM, NBS e alíquotas de referência (União, UF,
  município).

## Endpoints principais

Todos os caminhos começam em `http://localhost:8080/api/calculadora`.

| Funcionalidade | Endpoint |
|---|---|
| Cálculo de tributos (regime geral) | `POST /regime-geral` |
| Cálculo com observabilidade | `POST /observabilidade/regime-geral` |
| Descrição de código de erro | `GET /observabilidade/erros?codigo=REG-011` |
| Base de cálculo unificada NF-e/NFC-e | `POST /base-calculo/base-calculo-unificada` |
| Base de cálculo unificada NFS-e | `POST /base-calculo/base-calculo-unificada-nfse` |
| Geração de XML | `POST /xml/generate?tipo=nfe` |
| Validação de XML contra XSD | `POST /xml/validate?tipo=nfe&subtipo=grupo` |
| Situações tributárias (CBS/IBS) | `GET /dados-abertos/situacoes-tributarias/cbs-ibs` |
| Classificações tributárias | `GET /dados-abertos/classificacoes-tributarias/...` |
| Fundamentações legais | `GET /dados-abertos/fundamentacoes-legais` |
| NCM e NBS | `GET /dados-abertos/ncm`, `GET /dados-abertos/nbs` |
| Alíquotas de referência | `GET /dados-abertos/aliquota-uniao`, `/aliquota-uf`, `/aliquota-municipio` |

Exemplos de utilização da API estão em `references/exemplos.md` (nesta skill; cópia de `docs/exemplos.md` do repositório oficial).
A lista completa com esquemas e exemplos está no Swagger:
`http://localhost:8080/api/swagger-ui.html`.

## Requisitos

- Java 21 ou superior.
- Maven Wrapper (`mvnw` / `mvnw.cmd`) — não precisa instalar o Maven.
- Git para clonar o repositório.
- Windows, macOS ou Linux.

## Como executar

```bash
git clone https://github.com/ReceitaFederal/calculadora-rtc-regime-regular.git
cd calculadora-rtc-regime-regular
./mvnw spring-boot:run
```

A API sobe por padrão na porta `8080`.

## Repositório oficial

https://github.com/ReceitaFederal/calculadora-rtc-regime-regular

Este skill é mantido no ecossistema https://github.com/GambiarraFinance.

## English version

See `references/skill.en.md`.
