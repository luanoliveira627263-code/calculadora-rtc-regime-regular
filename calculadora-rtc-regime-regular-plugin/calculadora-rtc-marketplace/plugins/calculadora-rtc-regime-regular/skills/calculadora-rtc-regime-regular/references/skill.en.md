id: calculadora-rtc-regime-regular
name: Tax Calculator - General Regime (Brazilian Federal Revenue)
description: |
  Skill to integrate and use the General Regime Tax Calculator from the Brazilian
  Federal Revenue (Receita Federal do Brasil). It is a REST API (Java 21) that
  calculates CBS, IBS and Selective Tax (Consumption Tax Reform - LC 214/2025) in
  general regime operations, consults the official tables used in the calculation
  and generates and validates the taxation groups of electronic fiscal documents.
triggers: "calculate general regime taxes", "cbs ibs selective tax", "rtc general regime calculator", "brazilian federal revenue api general", "unified tax base nfe nfse", "xml nfe validate xsd", "cst tax classifications", "ncm nbs aliquotas"
---
# Tax Calculator - General Regime

## Overview

The General Regime Tax Calculator is an open REST API from the Brazilian Federal
Revenue (Receita Federal do Brasil) that calculates **CBS**, **IBS** and **Selective
Tax** (Consumption Tax Reform — LC 214/2025) for general regime operations,
consults the official tables used in the calculation and generates and validates
the taxation groups of electronic fiscal documents.

## When to use this skill

Use this skill when you need to:

- Calculate general regime taxes (the whole operation fails on the first error).
- Calculate with observability (per-item errors, without interrupting the others).
- Look up observability error codes (`REG-`).
- Calculate the unified tax base for NF-e/NFC-e and NFS-e.
- Generate XML from the calculation result.
- Validate XML (group or note) against the XSD.
- Look up CST and tax classifications (`cClassTrib`).
- Look up legal grounds, NCM, NBS and reference rates (Union, state, municipality).

## Main endpoints

All paths start at `http://localhost:8080/api/calculadora`.

| Feature | Endpoint |
|---|---|
| General regime tax calculation | `POST /regime-geral` |
| Calculation with observability | `POST /observabilidade/regime-geral` |
| Error code description | `GET /observabilidade/erros?codigo=REG-011` |
| Unified tax base NF-e/NFC-e | `POST /base-calculo/base-calculo-unificada` |
| Unified tax base NFS-e | `POST /base-calculo/base-calculo-unificada-nfse` |
| XML generation | `POST /xml/generate?tipo=nfe` |
| XML validation against XSD | `POST /xml/validate?tipo=nfe&subtipo=grupo` |
| Tax situations (CBS/IBS) | `GET /dados-abertos/situacoes-tributarias/cbs-ibs` |
| Tax classifications | `GET /dados-abertos/classificacoes-tributarias/...` |
| Legal grounds | `GET /dados-abertos/fundamentacoes-legais` |
| NCM and NBS | `GET /dados-abertos/ncm`, `GET /dados-abertos/nbs` |
| Reference rates | `GET /dados-abertos/aliquota-uniao`, `/aliquota-uf`, `/aliquota-municipio` |

API usage examples are in `docs/exemplos.md`. The complete list with schemas and
examples is in Swagger: `http://localhost:8080/api/swagger-ui.html`.

## Requirements

- Java 21 or higher.
- Maven Wrapper (`mvnw` / `mvnw.cmd`) — Maven does not need to be installed.
- Git to clone the repository.
- Windows, macOS or Linux.

## How to run

```bash
git clone https://github.com/ReceitaFederal/calculadora-rtc-regime-regular.git
cd calculadora-rtc-regime-regular
./mvnw spring-boot:run
```

The API starts by default on port `8080`.

## Official repository

https://github.com/ReceitaFederal/calculadora-rtc-regime-regular

This skill is maintained in the https://github.com/GambiarraFinance ecosystem.
