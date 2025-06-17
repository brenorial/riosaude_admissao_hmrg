# 📄 Explicação das Colunas Calculadas

## 1. Categorização de Enfermarias — `Enfermarias_HMRG`

### Objetivo

Classificar os setores assistenciais da base `vw_estatistica_mensal` em grupos macro de enfermarias, facilitando a análise por grandes áreas do hospital.

### Fórmula DAX

```DAX
Enfermarias_HMRG = 
SWITCH(
    TRUE(),
    
    'vw_estatistica_mensal'[hil_nmsecao] IN {
        "POSTO ASSISTENCIAL 51",
        "POSTO ASSISTENCIAL 53",
        "POSTO ASSISTENCIAL 52",
        "POSTO ASSISTENCIAL 54",
        "POSTO ASSISTENCIAL 34",
        "POSTO ASSISTENCIAL 35"
    }, "CLÍNICA MÉDICA",
    
    'vw_estatistica_mensal'[hil_nmsecao] IN {
        "POSTO ASSISTENCIAL 44",
        "POSTO ASSISTENCIAL 43",
        "POSTO ASSISTENCIAL 41",
        "POSTO ASSISTENCIAL 42",
        "POSTO ASSISTENCIAL 30",
        "POSTO ASSISTENCIAL 36",
        "POSTO ASSISTENCIAL 31"
    }, "CENTRO DE TERAPIA INTENSIVA",
    
    'vw_estatistica_mensal'[hil_nmsecao] IN {
        "POSTO ASSISTENCIAL 11",
        "POSTO ASSISTENCIAL 12"
    }, "CENTRO CIRÚRGICO",
    
    "OUTRAS"
)
```

### Explicação

Esta coluna classifica os registros segundo o campo `hil_nmsecao` em três grandes grupos:

* **Clínica Médica**
* **Centro de Terapia Intensiva (CTI)**
* **Centro Cirúrgico**

Registros que não se encaixam em nenhum dos grupos recebem o valor **"OUTRAS"**.

---

## 2. Categorização de Seções — `Seções_HMRG`

### Objetivo

Classificar os setores assistenciais da base `irs_fat_censo_ativo` em categorias maiores para análise agregada, incluindo setores que podem estar ativos ou inativos.

### Fórmula DAX

```DAX
Seções_HMRG = 
SWITCH(
    TRUE(),

    'irs_fat_censo_ativo'[secao_nome] IN {
        "POSTO ASSISTENCIAL 11",
        "POSTO ASSISTENCIAL 12"
    }, "CIRURGIA",

    'irs_fat_censo_ativo'[secao_nome] IN {
        "POSTO ASSISTENCIAL 30",
        "POSTO ASSISTENCIAL 31",  // CTI inativo, mas ainda categorizado
        "POSTO ASSISTENCIAL 36",
        "POSTO ASSISTENCIAL 41",
        "POSTO ASSISTENCIAL 42",
        "POSTO ASSISTENCIAL 43",
        "POSTO ASSISTENCIAL 44"
    }, "CTI",

    'irs_fat_censo_ativo'[secao_nome] IN {
        "POSTO ASSISTENCIAL 51",
        "POSTO ASSISTENCIAL 52",
        "POSTO ASSISTENCIAL 53",
        "POSTO ASSISTENCIAL 54",
        "POSTO ASSISTENCIAL 34",
        "POSTO ASSISTENCIAL 35",
        "POSTO ASSISTENCIAL 44",
        "POSTO ASSISTENCIAL 43",
        "POSTO ASSISTENCIAL 41",
        "POSTO ASSISTENCIAL 42",
        "POSTO ASSISTENCIAL 30",
        "POSTO ASSISTENCIAL 36",
        "POSTO ASSISTENCIAL 31"
    }, "INTERNAÇÃO",

    "Outros"
)
```

### Explicação

Essa coluna agrupa os setores em:

* **Cirurgia**
* **CTI** (incluindo postos que podem estar inativos)
* **Internação** (abrangendo diversos postos assistenciais, incluindo alguns que também constam no CTI)

Qualquer setor que não pertença a esses grupos recebe a categoria **"Outros"**.

---

## Observações comuns

* Ambas as colunas usam a função `SWITCH(TRUE(), ...)` que é uma forma de escrever múltiplas condições encadeadas.
* O uso de `IN {...}` facilita a verificação se o valor do campo está dentro de um conjunto específico de nomes de setores.
* As categorias criadas são úteis para segmentar e filtrar dados nos dashboards do Power BI.
