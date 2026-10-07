# Conexão e recuperação

| Sintoma | Próximo passo |
| --- | --- |
| MCP ausente | Abrir `/magic/mcp`, seguir o cliente escolhido e verificar conexão antes de tentar executar. |
| Claude web não autentica | Usar OAuth com **Registrar automaticamente**. A identidade publicada do Claude não é suportada pelo servidor atual. Em equipe, verificar instalação/permissões do administrador. |
| Claude Code não recebe o token | Confirmar a variável `ZAPMAGICO_MCP_TOKEN` no ambiente que iniciou o processo, sem imprimir seu valor. Abrir `/mcp`. |
| Sem ferramentas de escrita | A conexão pode ser `read`; indicar consentimento ou token de gestão. Não tentar elevar o escopo por parâmetros. |
| Conexão antes funcionava e agora retorna 401 | Verificar plano ativo/Liberty, expiração e revogação pelo painel. Renovar plano não exige fabricar outra identidade. Nunca afirmar a causa exata só pelo 401. |
| Sem saldo / limite de fotos ou produtos | Consultar plano/saldo e mostrar opções existentes. Recarga não libera MCP nem aumenta limites de pedidos. |
| Timeout, conexão interrompida ou resultado desconhecido | Consultar o recurso antes de repetir. A ação pode ter terminado no servidor. |

Para reconciliar: imagem/alteração → `product_get`; rascunho → `draft_get`/`drafts_list`; pedido → `orders_list`; checkout/assinatura → `billing_get` e painel do pagamento, lembrando que consultar saldo não prova que um checkout não foi criado. Para convite/mensagem sem consulta conclusiva, não reenviar automaticamente.

O servidor não garante idempotência para gerar, publicar, criar checkout ou enviar convite. Se não for possível confirmar o resultado, explique o estado desconhecido e pare a repetição dessa ação. Não exponha erros privados, credenciais ou contatos no diagnóstico.
