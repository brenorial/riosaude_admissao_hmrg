# 🗂️ Modelagem de Dados

Este documento descreve a estrutura da base de dados utilizada no projeto, suas tabelas principais e a lógica de transformação aplicada para alimentar o dashboard.

---

## Fonte de Dados

- View para historico: `vw_estatistica_mensal`
- View para censo: `irs_fat_censo_ativo`
- Dados extraídos diretamente do sistema hospitalar de gestão
- Contém informações sobre pacientes internados, leitos, setores, datas e status clínicos

---

## Transformações

- Criação da coluna calculada `Enfermarias_HMRG` para categorização de setores
- Filtros para ignorar registros inválidos ou vazios
- Medidas DAX para contagem e sumarização por setores
