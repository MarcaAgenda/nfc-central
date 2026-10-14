# NFC Central

Sistema estático para cadastrar plaquinhas NFC com links de Google Avaliações, Instagram, WhatsApp, cardápio, localização e agendamento.

## Publicar com GitHub Pages

1. Abra **Settings → Pages** neste repositório.
2. Em **Build and deployment**, escolha **Deploy from a branch**.
3. Em **Branch**, selecione `main` e `/(root)` e clique em **Save**.
4. Após a publicação, confirme se a página abre em: https://marcaagenda.github.io/nfc-central/
5. Painel administrativo (modo de preparação dos cadastros): https://marcaagenda.github.io/nfc-central/?admin

## Como cadastrar e publicar

1. No painel, escolha **Nova empresa**, preencha nome, identificador e URLs.
2. Salve o rascunho e abra **Links** para gerar a URL da plaquinha ou QR Code.
3. Clique em **Baixar clientes.json**.
4. Substitua o conteúdo de `data/clientes.json` pelo arquivo exportado e faça commit na branch `main`.
5. Aguarde a atualização do site e teste a URL pública em mais de um celular.

O painel NÃO tem login próprio nem salva mudanças direto no repositório: apenas prepara os dados no navegador e exporta o JSON. Qualquer pessoa pode abrir o painel, mas só colaboradores do GitHub conseguem efetivamente publicar alterações no site.

## Exemplos de URLs

- Página da empresa: `https://marcaagenda.github.io/nfc-central/?empresa=demo`
- Instagram direto: `https://marcaagenda.github.io/nfc-central/?empresa=demo&acao=instagram`
- Google direto: `https://marcaagenda.github.io/nfc-central/?empresa=slug-da-empresa&acao=google`

Não renomeie o repositório nem altere identificadores de empresas que já estejam em NFCs bloqueados. Antes de bloquear uma tag, teste se ela lê a URL completa e se o destino funciona.

Os cadastros no JSON são públicos: não coloque senhas, dados pessoais não destinados à divulgação nem outras informações confidenciais. Para o Google, peça ao responsável o link oficial em **Perfil da Empresa → Receber mais avaliações**. Avaliações devem ser espontâneas e reais.

## Limitações da versão 1

- Controle de publicação pela conta GitHub, não por senha no painel.
- Sem banco de dados privado, pagamentos, métricas de visitas ou sincronização automática.
- QR Code usa o serviço externo api.qrserver.com para renderizar códigos; não coloque dados sigilosos nas URLs.
- A versão inicial vem com empresa fictícia de demonstração, cujo link de Instagram aponta para o perfil utilizado no teste. Troque quando desejar.
