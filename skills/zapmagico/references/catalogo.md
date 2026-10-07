# Loja e catálogo por conversa

Use para pedidos como “monte minha loja com base no negócio que conversamos”. O MCP opera uma loja já criada e vinculada à conta; não cria a conta do cliente nem acessa histórico inteiro do assistente.

1. Consulte `store_get`, `products_list` e, se houver geração integrada, `billing_get`. Preserve produtos, links e WhatsApp existentes.
2. Extraia do briefing nome, público, produtos, preços, variações e entrega. Confirme apenas informações essenciais que faltarem. Não crie características comerciais como se fossem fatos.
3. Configure os campos solicitados com `store_update`; crie novas ofertas como `draft` usando `product_create`. Mantenha os IDs retornados, sem procurar ofertas pelo título como substituto do ID.
4. Escolha a origem das imagens conforme [imagens.md](imagens.md). Se o usuário já escolheu, siga a escolha. Prepare uma identidade coerente e uma composição específica por oferta; não substitua capas comerciais por cartões tipográficos improvisados.
5. Consulte `product_get`, confira os dados, a galeria e a capa. Abra a imagem antes de afirmar que a revisou. Se a geração foi salva mas a capa falhou, reordene a imagem existente.
6. Publique com `product_update` quando houver autorização e dados suficientes, preservando os campos completos. Sem autorização, apresente os rascunhos para revisão.
7. Informe URL da vitrine, produtos criados/alterados e pendências. Não invente entrega automática de produtos digitais: descreva o fluxo existente e confirme o que falta.

O prompt MCP `catalogo_com_design_magico`, quando disponível, ajuda nesse fluxo. Limites de produtos, fotos e gerações continuam válidos pelo MCP.

## Exemplos de pedido

- “Monte o catálogo do meu negócio a partir desta conversa. Confirme preços e entrega, prepare rascunhos e deixe para eu revisar.”
- “Crie três ofertas para estas camisetas com tamanhos P/M/G. Use meus preços e preserve as ofertas existentes.”
- “Melhore a descrição desta oferta mantendo preço, slug, fotos, desconto e variações.”
