# Imagens com a identidade da loja

## Gerar no próprio ChatGPT

Use quando o usuário escolher a geração nativa do cliente, se ela estiver disponível.

1. Consulte `product_image_prompt` com o ID da oferta, estilo `infographic`, `lifestyle` ou `macro`, e feedback opcional. `referenceMode: "auto"` usa a referência existente; `"none"` não retorna referência.
2. Use `prompt`, `referenceImageUrl` e `referenceNote`. O prompt usa os mesmos templates, cores e dados do Design Mágico. Sem foto, ignore instruções do template sobre foto anexada e confirme a direção visual; não invente a aparência do produto.
3. Gere com a ferramenta nativa de imagens do cliente apenas se ela existir. O preparo do prompt não consome saldo ZapMágico; a geração obedece aos limites da conta do cliente. Não prometa geração nativa no Claude ou Claude Code.
4. Envie o resultado por `media_upload` somente se tiver acesso aos bytes reais. Confira o schema: base64, até 2 MB por arquivo e 3 MB no total. O servidor não baixa URLs externas. Não invente base64, não converta links `sandbox:` em URLs públicas e não tente buscar arquivos privados por URL.
5. Se o cliente não permitir transferir o arquivo, oriente o usuário a baixar a imagem e fazer upload na oferta. Não substitua esse caminho por geração integrada cobrada sem autorização.
6. Consulte a oferta, confira a galeria e ajuste a ordem com `product_reorder_images` se necessário. O upload não garante promoção automática a capa.

## Design Mágico integrado

Use quando a geração integrada estiver autorizada. Consulte saldo/limites quando necessário e chame `product_create_image`.

- `style`: `infographic`, `lifestyle`, `macro` ou `custom`.
- `customPrompt`: direção visual, público, composição e texto curto; não invente fatos comerciais.
- `referenceMode: "auto"`: usa a imagem existente; `"none"`: direção nova, útil em produto digital ou redesign sem referência aproveitável.
- `setAsCover: true`: padrão, promove a geração a capa sem apagar a galeria.

A IA da plataforma usa 1 geração do saldo por imagem. Liberty com chave própria compatível é cobrada pelo provedor, sem desconto do saldo da plataforma. OAuth não transfere assinatura ChatGPT/Claude para nossa API.

Confira `imageId`, `imageUrl` e `coverSet`. Abra a imagem para revisar composição, texto e correspondência à oferta. Se a promoção a capa falhar, use a imagem salva e reordene; não gere de novo só para corrigir a capa.

Após timeout ou `operation_outcome_unknown`, consulte a galeria antes de qualquer nova geração. Se o estado não puder ser confirmado, informe a pendência e não repita automaticamente.
