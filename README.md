# Porto Baby Care — Landing page

Página única, responsiva e mobile-first: menu hambúrguer, botão flutuante de WhatsApp, formulário de disponibilidade, serviços, como funciona, sobre, galeria de momentos, FAQ e CTA final.

## Rodar localmente

```sh
cd porto-baby-care
python3 -m http.server 8767
```

Acesse `http://localhost:8767`.

## Arquivos

- `index.html` — HTML, CSS e JS embutidos (sem dependências de build).
- `assets/hero.jpg`, `assets/praia.jpg` — fotos do Pexels salvas localmente.
- `assets/logo-marca.png` — emblema oficial da marca, usado no cabeçalho.
- `assets/logo-oficial.png` — logo completa enviada pelo cliente, com fundo preto removido, usada no rodapé.
- `assets/cuidadora.png` — foto da profissional com a criança, usada em "Sobre Nós".
- `assets/galeria/f01.jpg` a `f23.jpg` — fotos de crianças já atendidas, usadas na galeria "Momentos". Todas as publicações foram autorizadas previamente pelos pais; o aviso aparece no topo da seção.

## Antes de publicar

- Substitua `WHATSAPP` no topo do `<script>` em `index.html` pelo número real (DDI + DDD + número, apenas dígitos). Hoje é um número de exemplo.
- Ajuste textos, endereço e links das redes sociais conforme o negócio.

## Pontos de integração com o backend

- `form.addEventListener("submit", ...)` em `index.html`: hoje valida os campos e abre o WhatsApp com a mensagem pronta. É aqui que a chamada à API de disponibilidade deve entrar.
- `const WHATSAPP`: centraliza o destino de todos os botões "Fale Conosco"; pode virar configuração vinda do backend.
- Campos enviados: `data` (date), `hospedagem` (hotel/resort/pousada/imóvel de temporada), `idade` (faixa etária).

## Créditos das fotos

- Hero: https://www.pexels.com/photo/4149006/
- Praia de Porto de Galinhas: https://www.pexels.com/photo/40907074/
- Logo, foto da profissional e galeria de momentos: assets enviados pelo cliente.

## Avaliações

A seção "Quem já foi, conta" contém seis depoimentos de exemplo, com nomes e textos ilustrativos. Substitua por avaliações reais de clientes antes de publicar — os textos atuais não são depoimentos autênticos.

## Fluxo de disponibilidade

- `index.html`: o campo "Em qual hotel/resort você está?" é de texto livre. Ao enviar, a página redireciona para `disponibilidade.html?data=...&local=...&idade=...`.
- `disponibilidade.html`: mostra a barra de carregamento e, ao terminar, exibe "Busca concluída!" com a quantidade sorteada de babás para essa data e o botão para entrar em contato com um resumo dos dados informados.
- O botão "Entrar em contato" abre `https://wa.me/5581992455112` com quantidade de babás, data, local e idade já preenchidos na mensagem.
- A quantidade de babás é sorteada entre 1 e 4 a cada consulta (texto no singular quando é 1). Resultado e tempo de carregamento são simulações; troque pela resposta real do backend quando a API estiver pronta.
