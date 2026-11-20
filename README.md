# Yooo – Milkshakes

Landing page de uma loja de milkshakes inspirada em cafeterias como a Starbucks. O cliente escolhe os sabores, monta o carrinho e finaliza o pedido pelo WhatsApp, com uma mensagem já estruturada para agilizar o atendimento.

## Descrição curta

> Landing page de milkshakes com vitrine animada, carrinho e finalização de pedido pelo WhatsApp, com validação de nome e CEP (entregas apenas na cidade de São Paulo). HTML, CSS e JavaScript puros, em um único arquivo.

## Funcionalidades

- **Hero** com foto do produto e chamada para a vitrine.
- **Os 3 campeões:** cards com os sabores mais vendidos, ligados à vitrine.
- **Vitrine em carrossel:** navegação por setas, miniaturas, teclado (← →) e arrastar no celular, com animações em GSAP.
- **Tamanhos e preços:** cada sabor tem 350 ml e 500 ml, com valor próprio.
- **Carrinho:** adicionar, aumentar, diminuir e remover itens, com total atualizado.
- **Formulário de finalização:** pede nome e CEP antes de abrir o WhatsApp.
  - Nome: mínimo de 2 letras, sem números.
  - CEP: máscara `00000-000`, 8 dígitos e validação de área de entrega.
  - CEP fora da área mostra "Ainda não fazemos entregas a esse endereço" e permite digitar outro.
- **Mensagem pronta no WhatsApp:** nome, CEP, sabores, tamanhos, quantidades, valores e total.
- **Dúvidas frequentes** em acordeão.
- **Responsivo**, com suporte a tema claro e escuro no navegador.

## Exemplo da mensagem enviada

```
Olá, Yooo! Meu nome é Ana Souza.
CEP de entrega: 01310-100

*Meu pedido:*
• 2x Lotus Crocante (500 ml) – R$ 69,80
• 1x Morango Cremoso (350 ml) – R$ 19,90

*Total: R$ 89,70*
```

## Tecnologias

- HTML, CSS e JavaScript puros (sem build, sem dependências para instalar)
- [GSAP 3.12.5](https://gsap.com/) via CDN (animações do carrossel e do carrinho)
- Fonte Baloo 2 via Google Fonts
- Imagens em WebP embutidas no próprio HTML (base64)

## Como rodar

Não precisa instalar nada. Abra o arquivo `Yooo-site.html` (ou `index.html`) no navegador. É necessário estar conectado à internet, porque o GSAP e a fonte vêm de CDN.

## Configuração

As configurações ficam no começo do `<script>`:

```js
var WHATS = "5511999999999"; // 55 + DDD + número da loja
function cepSP(n){ ... }     // faixas de CEP atendidas
```

- **WhatsApp:** troque `WHATS` pelo número real da loja.
- **Área de entrega:** `cepSP` aceita a capital de São Paulo, nas faixas 01000-000 a 05999-999 e 08000-000 a 08499-999. Para atender outras regiões, ajuste ou acrescente faixas.
- **Rodapé:** telefone, horário, Instagram e TikTok são textos de exemplo e devem ser trocados no HTML.

### Sabores

Os sabores ficam no array `D`:

```js
{ n:"Lotus Crocante", t1:"Lotus", t2:"Crocante",
  p:[27.9, 34.9],              // preços: 350 ml e 500 ml
  ing:["Biscoito Lotus", "..."],
  d:"Descrição do sabor.",
  ac:"#f0c27c" }               // cor do arco de fundo na vitrine
```

As fotos ficam no array `IMG`, **na mesma ordem** do array `D`. Para trocar uma foto, recorte o produto com fundo transparente, converta para WebP (largura de cerca de 400 px) e coloque como `data:image/webp;base64,...` na posição correspondente.

## Publicar na Vercel

1. Renomeie `Yooo-site.html` para `index.html` e deixe-o sozinho numa pasta.
2. Na pasta, rode `npx vercel` (ou `npx vercel --prod` para o endereço definitivo).
3. Ou suba a pasta para um repositório no GitHub e importe em vercel.com (Add New → Project → Deploy). Não precisa de configuração.

Qualquer hospedagem de arquivos estáticos funciona (Netlify, GitHub Pages etc.).

## Limitações conhecidas

- A validação do CEP só confere as faixas numéricas. Ela não verifica se o CEP existe nem se o endereço está dentro da área real de entrega.
- Não há pagamento nem back-end. O pedido é só uma mensagem no WhatsApp, e a confirmação e o pagamento são combinados com a loja.
- O carrinho não é salvo: recarregar a página esvazia o carrinho.
- Se o navegador bloquear a janela do WhatsApp, o site abre o link na mesma aba.

## Próximos passos sugeridos

- Seção "Quem somos" (apresentação da marca).
- Novas perguntas na seção de dúvidas.
- Campo opcional de observações no pedido.
- Número do WhatsApp e redes sociais reais.

## Licença

Projeto privado da Yooo. Todos os direitos reservados.
