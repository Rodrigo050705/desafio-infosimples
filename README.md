# 🌌 Starships E-commerce Web Scraper - Desafio Infosimples

[![Python Version](https://img.shields.io/badge/python-3.12-blue.svg)](https://www.python.org/)
[![BeautifulSoup](https://img.shields.io/badge/library-BeautifulSoup4-green.svg)](https://www.crummy.com/software/BeautifulSoup/bs4/doc/)

Este projeto é um desafio de **Web Scraping** desenvolvido em Python dentro do ambiente Google Colab. O objetivo principal é extrair dados estruturados de páginas de produtos de um e-commerce de naves espaciais (inspirado no universo Star Wars) e convertê-los em um formato JSON limpo, tipado e padronizado.

## 🚀 Funcionalidades

O scraper é capaz de mapear e extrair com precisão diversas informações de uma página de produto. Algumas delas são:
* **Breadcrumbs (Trilha de Navegação):** Captura a árvore hierárquica de categorias do produto transformando-a em uma lista sequencial.
* **Blocos de Descrição:** Extração inteligente de múltiplos parágrafos de texto puro, tratando quebras de linha e caracteres de escape.
* **Especificações Técnicas (Primárias e Secundárias):** Mapeamento dinâmico de tabelas de atributos genéricas (sem classes identificadoras) usando lógica de posicionamento de colunas (`label` e `value`).
* **Variações do Produto:** Mapeamento completo de submodelos e configurações, incluindo:
  * Captura de nomes e status de disponibilidade transformados em booleanos (`True`/`False`).
  * Tratamento e conversão de preços no formato brasileiro (`R$ 4.799.990,00`) diretamente para tipos numéricos (`float`), facilitando análises futuras.

## 🛠️ Tecnologias Utilizadas

* **[Python 3.12](https://www.python.org/)** - Linguagem base do projeto.
* **[BeautifulSoup 4 (bs4)](https://www.crummy.com/software/BeautifulSoup/bs4/doc/)** - Biblioteca utilizada para parsing e navegação na árvore DOM do HTML.
* **[Requests](https://requests.readthedocs.io/)** - Utilizada para requisições HTTP e captura do HTML bruto das páginas.
* **[JSON](https://docs.python.org/3/library/json.html)** - Biblioteca nativa para estruturação, formatação e exportação dos dados coletados.

## 💻 Como Testar?
* Abra seu ambiente no google colab
* Certifique_se de instalar/atualizar as versões corretas das bibliotecas: !pip install beautifulsoup4 requests
* Cole o código do script no notebook
* Execute a célula para iniciar a requisição e a extração dos dados
* O arquivo JSON formatado será exibido no console ou poderá ser salvo direto no seu ambiente de arquivos do Colab
  
## 📋 Estrutura do JSON Gerado

Os dados extraídos são consolidados em um arquivo ou saída JSON seguindo este modelo estrito: 

```json
{
    "title": "Corellian YT-1300f Light Freighter",
    "brand": "Corellian Engineering Corporation",
    "categories": [
        "Stellarcraft",
        "Spacecraft",
        "Freighters",
        "Corellian Engineering",
        "Corellian YT-1300f light freighter"
    ],
    "description": "Seja bem-vindo ao maior negócio do setor galáctico. Apresentamos o YT-1300 light freighter: a nave mais rápida da galáxia, agora disponível para aquisição direta no maior marketplace interestelar do Brasil. Esta unidade pertenceu a apenas um proprietário anterior, um carismático contrabandista corelliano que garantiu que ela \"quase nunca precisou de manutenção\". As pequenas marcas de tiro de canhão laser e o sistema de ejeção de compartimento de carga levemente modificado são features, não bugs.\nA Millennium Falcon, uma YT-1300f modificada, completou a Rota Kessel em impressionantes 12 parsecs, uma marca que os engenheiros da Corellian Engineering Corporation ainda não conseguem explicar fisicamente, mas garantimos ser real. O casco é composto de ligas tibanianas de alta resistência com reparos feitos à mão pelos melhores mecânicos que Mos Eisley tem a oferecer. O sistema de propulsão inclui dois motores iônicos Girodyne SRB42 altamente modificados, que transformam uma nave de carga comum em algo que até os caças TIE têm dificuldade em alcançar. Não nos responsabilizamos por ordens de captura ativas, entreveros imperiais ou carga de origens duvidosas encontrada a bordo.",
    "skus": [
        {
            "name": "Standard Configuration",
            "current_price": 4799990.0,
            "old_price": 5999990.0,
            "available": true
        },
        {
            "name": "Battle-Ready Configuration",
            "current_price": null,
            "old_price": null,
            "available": false
        },
        {
            "name": "Smuggler's Special(pre-owned, 1 careful owner)",
            "current_price": 3499990.0,
            "old_price": null,
            "available": true
        }
    ],
    "specification": [
        {
            "label": "Hyperdrive Class",
            "value": "0.5 (Modified)"
        },
        {
            "label": "Crew Capacity",
            "value": "2 (+ 1 Wookiee co-pilot recommended)"
        },
        {
            "label": "Armament",
            "value": "2x Quad laser cannons, 2x Blaster cannons"
        },
        {
            "label": "Shield Generator",
            "value": "Novaldex particle shield"
        },
        {
            "label": "Kessel Run Record",
            "value": "12 parsecs"
        },
        {
            "label": "Previous Owner",
            "value": "One careful Corellian smuggler"
        },
        {
            "label": "Fuel Type",
            "value": "Tibanna gas"
        },
        {
            "label": "Planet of Origin",
            "value": "Corellia"
        },
        {
            "label": "Recyclable?",
            "value": "Not recommended"
        },
        {
            "label": "Carbon Footprint",
            "value": "Classified"
        },
        {
            "label": "Sublight Engines",
            "value": "2x Girodyne SRB42 ion engines"
        },
        {
            "label": "Sensor Range",
            "value": "200,000 km"
        },
        {
            "label": "Detention Block",
            "value": "Not included"
        },
        {
            "label": "Cloaking Device",
            "value": "No"
        },
        {
            "label": "Self-Destruct System",
            "value": "Questionable condition"
        },
        {
            "label": "Escape Pods",
            "value": "2 (1 functional)"
        },
        {
            "label": "Artificial Gravity",
            "value": "Yes"
        },
        {
            "label": "Cooling System",
            "value": "Temperamental but operational"
        }
    ],
    "reviews": [
        {
            "name": "Leia O.",
            "date": "12/02/2026",
            "score": 5,
            "text": "Salvou a Rebelião. Compraria novamente. A nave chegou mais rápido do que o esperado; o tempo da Rota Kessel listado é preciso."
        },
        {
            "name": "Jabba H.",
            "date": "29/02/2026",
            "score": 2,
            "text": "O vendedor me deve dinheiro. O compartimento de carga estava vazio quando chegou. Não recomendo o proprietário anterior."
        },
        {
            "name": "Rey S.",
            "date": "08/04/2026",
            "score": 4,
            "text": "A nave se manteve inteira apesar das minhas preocupações iniciais. A Força estava comigo nesta compra. Pequeno problema na hidráulica ao pousar mas nada que um empurrão da Força não resolva."
        }
    ],
    "reviews_average_score": 3.7,
    "url": "https://infosimples.com/vagas/desafio/stellarcraft/product.html"
}
