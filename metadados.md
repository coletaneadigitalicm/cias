# Estrutura do `metadados.json`

## Objetivo
Este documento descreve a estrutura em camadas do arquivo `metadados.json`, que é publicado neste repositório para disponibilizar publicamente os metadados dos louvores, seus arranjos e materiais associados.

## Visão geral em camadas
- **Camada 1 — Louvor (`louvor`)**: reúne as informações principais de um louvor específico.
- **Camada 2 — Arranjos (`arranjos`)**: lista cada arranjo disponível para o louvor.
- **Camada 3 — Materiais (`materiais`)**: agrega os recursos vinculados a um arranjo, como partituras, áudios ou vídeos.

## Exemplo estrutural
```json
{
  "nome": "nomeDoRepositorio",
  "versao": "0.1.0",
  "louvor": {
    "id": "idLouvor",
    "nome": "nomeLouvor",
    "outrosNomes": ["nomeAlternativo1", "nomeAlternativo2"],
    "arranjos": [
      {
        "titulo": "tituloArranjo",
        "dataUltimaAlteracao": "2025-10-02",
        "materiais": [
          {
            "titulo": "tituloMaterial",
            "categoria": "categoriaMaterial",
            "tipo": "pdf",
            "url": "https://link.para/o/material.pdf"
          }
        ]
      }
    ]
  }
}
```

## Detalhamento dos campos
### Objeto `louvor`
| Campo | Tipo | Obrigatório | Descrição |
| ----- | ---- | ----------- | --------- |
| `id` | string | Sim | Identificador único e estável do louvor. Pode ser numérico ou alfanumérico, desde que não contenha espaços. |
| `nome` | string | Sim | Nome principal do louvor que será exibido ao público. |
| `outrosNomes` | array de strings | Não | Lista de variações ou títulos alternativos. Use uma lista vazia (`[]`) quando não existirem outros nomes. |
| `arranjos` | array de objetos | Sim | Conjunto de arranjos publicados para o louvor. Deve conter pelo menos um arranjo válido. |

### Objetos em `arranjos`
| Campo | Tipo | Obrigatório | Descrição |
| ----- | ---- | ----------- | --------- |
| `titulo` | string | Sim | Nome do arranjo, usado para diferenciar múltiplas versões do mesmo louvor. |
| `dataUltimaAlteracao` | string | Sim | Data da última atualização do arranjo. Recomenda-se usar o formato ISO 8601 (`AAAA-MM-DD`). |
| `materiais` | array de objetos | Sim | Lista de materiais associados ao arranjo. Se não houver materiais, use uma lista vazia (`[]`) e atualize-a assim que novos recursos estiverem disponíveis. |

### Objetos em `materiais`
| Campo | Tipo | Obrigatório | Descrição |
| ----- | ---- | ----------- | --------- |
| `titulo` | string | Sim | Título legível do material, como "Partitura SATB" ou "Áudio de Referência". |
| `tipo` | string | Sim | Classificação do tipo de material. Valores comuns: `pdf`, `audio`, `texto`, `youtube`. Outros tipos podem ser adicionados conforme necessário. |
| `url` | string | Sim | Endereço público para acessar o material. Prefira URLs HTTPS e verifique periodicamente se continuam válidas. |
| `categoria` | string | Sim | Indica a seção ou grupo para o qual o material é destinado (ex.: `coro`, `flauta`, `gesto`). É possível ampliar a lista de categorias conforme novos materiais surgirem. |

## Convenções e boas práticas
- Mantenha os arrays ordenados de forma coerente (por exemplo, arranjos por data mais recente ou materiais por relevância).
- Atualize `dataUltimaAlteracao` sempre que um arranjo ou qualquer material ligado a ele sofrer modificações.
- Utilize valores consistentes para `tipo` e `categoria` para facilitar filtragens futuras.
- Valide os links de `url` antes de publicar alterações para evitar referências quebradas.

## Publicação do `metadados.json`
O propósito deste repositório é disponibilizar o arquivo `metadados.json` publicamente. Ao atualizar os metadados, garanta que o arquivo se mantenha acessível, bem formatado e coerente com esta documentação.
