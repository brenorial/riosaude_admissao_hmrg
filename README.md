# 🏥 Projeto Power BI - Dashboard de Leitos do Hospital Municipal Ronaldo Gazolla (HMRG)

## 🎯 Objetivo do Projeto:

Criar um **Dashboard interativo no Power BI** para o acompanhamento da ocupação e movimentação dos leitos hospitalares do HMRG, permitindo uma **visão rápida e gerencial da situação dos leitos**, por setores e perfis de internação.

---

## 📊 Principais Métricas da Base:

A base utilizada (`vw_estatistica_mensal`) contém informações de produção hospitalar, internações e setores de atendimento.

### Métricas calculadas:

| Métrica                                | Descrição                                                                                                                                 |
| -------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| **Total de Internados**                | Quantidade total de pacientes internados no período analisado                                                                             |
| **Internados por Enfermaria**          | Separação por tipo de enfermaria: **Clínica Médica**, **Centro de Terapia Intensiva (CTI)**, **Centro Cirúrgico**, **Outras Enfermarias** |
| **Taxa de Ocupação**                   | Percentual de leitos ocupados em relação ao total de leitos disponíveis                                                                   |
| **Entradas no Mês**                    | Total de novos internados no mês                                                                                                          |
| **Altas no Mês**                       | Total de pacientes que tiveram alta no mês                                                                                                |
| **Tempo Médio de Permanência (TMP)**   | Média de dias de permanência dos pacientes internados                                                                                     |
| **Internações por Perfil de Paciente** | Divisão por Adulto / Pediátrico (se aplicável na base)                                                                                    |
| **Evolução Mensal da Ocupação**        | Tendência de ocupação ao longo dos meses                                                                                                  |
| **Giro de Leitos**                     | Quantidade de vezes que cada leito foi ocupado no mês                                                                                     |

---

## 🏷️ Campos Criados na Modelagem:

| Campo Calculado                             | Função                                                                                     |
| ------------------------------------------- | ------------------------------------------------------------------------------------------ |
| **Enfermarias\_HMRG**                       | Agrupa os setores em categorias (CM, CTI, CC, Outras) para facilitar análise               |
| **Quant Internados CM / CTI / CC / Outras** | Contadores ou somatórios por tipo de enfermaria                                            |
| **Taxa de Ocupação por Setor**              | Métrica % calculada a partir do total de internados dividido pelo total de leitos do setor |

---

## ✅ Exemplos de Visualizações no Dashboard:

* 📈 **Gráfico de Evolução Mensal da Ocupação**
* 🧱 **Cartões de KPIs**: Total de Internados, Altas, TMP, Ocupação %
* 🏥 **Gráfico de Barras**: Quantidade de Internados por Enfermaria
* 📆 **Tabela Dinâmica**: Detalhamento por setor e mês
* 📉 **Tendência de Internações Mensais**

---