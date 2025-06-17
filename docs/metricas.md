
# 📊 Métricas Criadas - Dashboard de Leitos HMRG

Este documento detalha as principais **métricas DAX** desenvolvidas na base de dados `vw_estatistica_mensal` para o projeto do **Dashboard de Leitos do Hospital Municipal Ronaldo Gazolla (HMRG)**.

---

## ✅ 1. Quantidade de Internados por Enfermaria

Métricas criadas para contar o número de internados por tipo de enfermaria.

### 1.1 Quant Internados CM (Clínica Médica):

```DAX
Quant Internados CM = 
CALCULATE(
    COUNT(vw_estatistica_mensal[internado]),
    FILTER(
        vw_estatistica_mensal,
        vw_estatistica_mensal[Enfermarias_HMRG] = "CLÍNICA MÉDICA" &&
        NOT(ISBLANK(vw_estatistica_mensal[internado]))
    )
)
```

---

### 1.2 Quant Internados CTI:

```DAX
Quant Internados CTI = 
CALCULATE(
    COUNT(vw_estatistica_mensal[internado]),
    FILTER(
        vw_estatistica_mensal,
        vw_estatistica_mensal[Enfermarias_HMRG] = "CENTRO DE TERAPIA INTENSIVA" &&
        NOT(ISBLANK(vw_estatistica_mensal[internado]))
    )
)
```

---

### 1.3 Quant Internados CC (Centro Cirúrgico):

```DAX
Quant Internados CC = 
CALCULATE(
    COUNT(vw_estatistica_mensal[internado]),
    FILTER(
        vw_estatistica_mensal,
        vw_estatistica_mensal[Enfermarias_HMRG] = "CENTRO CIRÚRGICO" &&
        NOT(ISBLANK(vw_estatistica_mensal[internado]))
    )
)
```

---

### 1.4 Quant Internados Outras:

```DAX
Quant Internados Outras = 
CALCULATE(
    COUNT(vw_estatistica_mensal[internado]),
    FILTER(
        vw_estatistica_mensal,
        vw_estatistica_mensal[Enfermarias_HMRG] = "OUTRAS" &&
        NOT(ISBLANK(vw_estatistica_mensal[internado]))
    )
)
```

---

## ✅ 2. Total Geral de Internados:

Soma total de todos os internados, independente da enfermaria.

```DAX
Total Internados = 
CALCULATE(
    COUNT(vw_estatistica_mensal[internado]),
    NOT(ISBLANK(vw_estatistica_mensal[internado]))
)
```

---

## ✅ 3. Lógica comum aplicada em todas as medidas:

* Todas as contagens consideram apenas **registros com valor válido em `[internado]`**, ou seja, **não nulos**.
* As segmentações por enfermaria dependem diretamente do campo calculado `Enfermarias_HMRG`.

---

## ✅ 4. Próximas Métricas Planejadas:

| Métrica                    | Descrição                              |
| -------------------------- | -------------------------------------- |
| Taxa de Ocupação           | Proporção de leitos ocupados por setor |
| Tempo Médio de Permanência | Média de dias internados por paciente  |
| Altas no Mês               | Total de pacientes com alta            |
| Giro de Leitos             | Número de internações por leito no mês |

---

