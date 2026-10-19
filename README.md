# NFC Central 2.0

Sistema de páginas públicas, inventário de placas/cartões/tags NFC e painel de edição. Hospedado no GitHub Pages, com um arquivo JSON versionado no repositório.

## Acessar

- Site: https://marcaagenda.github.io/nfc-central/
- Painel: https://marcaagenda.github.io/nfc-central/painel/
- Página de demonstração: https://marcaagenda.github.io/nfc-central/?empresa=demo
- Página Pix antiga (mantida): https://marcaagenda.github.io/nfc-central/pix/

## Como usar (passo a passo)

1. Abra o painel e vá em **Páginas → Nova página**. Escolha um modelo (loja, barbearia, restaurante, profissional ou Pix).
2. Preencha nome, descrição, links HTTPS, cor/tema e foto opcional. Clique em **Salvar alterações**.
3. Vá em **Tags e placas**. Cadastre NFCs individualmente ou use **Cadastrar várias NFCs de uma vez** (por exemplo, 50 adesivos).
4. Abra a NFC, escolha **Editar** e selecione a página vinculada; configure o status como **Ativa**. Salve.
5. Abra **Link / QR** da NFC, copie a URL com `?tag=...` e **grave esse endereço na tag física** usando um gravador NFC. O identificador não muda ao trocar o destino da tag.
6. Vá em **Publicar**, conecte o GitHub e clique em **Publicar alterações**. Confira as URLs no celular após a publicação.

> Atenção: o botão **Salvar alterações** prepara o rascunho local. Os dados só aparecem para os clientes quando você **Publicar no GitHub**. Sem conexão, você pode usar **Baixar backup** e editar seus rascunhos.

## Conectar ao GitHub para publicar sem baixar arquivos

Crie um Fine-grained Personal Access Token em https://github.com/settings/personal-access-tokens/new :

- **Resource owner:** `MarcaAgenda`
- **Repository access:** Only select repositories → `nfc-central`
- **Repository permissions:** Contents → **Read and write**
- **Metadata:** Read (permissão implícita)
- Defina expiração e copie o token para o campo **Painel → Publicar**.

O token é enviado **somente para a API oficial do GitHub pelo navegador** e fica **somente na memória da aba**. Não é salvo em arquivo, `localStorage` nem no repositório. É preciso informar novamente ao reabrir. **Nunca envie token por WhatsApp, chat ou GitHub.**

## Links permanentes

- **Página**: `https://marcaagenda.github.io/nfc-central/?empresa=nome-da-empresa`
- **Tag** (recomendado gravar na NFC): `https://marcaagenda.github.io/nfc-central/?tag=tag-001`
- **Página com destino específico** (compatível com o sistema antigo): `?empresa=nome-da-empresa&acao=google`

O arquivo `data/clientes.json` armazena páginas e tags. Cada tag tem ID, tipo, status, página vinculada e observação pública. Não é possível alterar IDs das tags já existentes pelo painel, para evitar links quebrados.

Os QR Codes são renderizados usando uma API pública externa (`api.qrserver.com`) e expõem apenas o link público da página ou tag.

## Funcionalidades incluídas

- Criar, editar, pausar, excluir e duplicar páginas;
- Temas azul, escuro, laranja, bege, verde e roxo;
- Botões padrão para Google Avaliações, Instagram, WhatsApp, Maps, cardápio, agendamento, site e Pix;
- Até 15 botões personalizados por página;
- Controle individual de etiquetas, cartões e placas NFC, inclusive lotes de até 200 unidades por vez;
- Reatribuir a mesma NFC a outra empresa sem regravar a tag;
- QR Code individual por página/tag, copiar URL e testar abertura;
- Backup/importação JSON, rascunho local, publicação via GitHub com detecção de conflito de versão.

## Limitações desta versão

- Este é um **sistema estático com publicação protegida pelo GitHub**, não um SaaS completo com autenticação própria.
- Não há métricas reais de leitura, cobrança mensal ou áreas separadas por cliente. Elas exigem backend e banco de dados.
- `data/clientes.json` é **público**. Não cadastre documentos, dados confidenciais, senhas, telefones privados ou informações sensíveis nas observações.
- A geração de QR Code usa serviço externo. Para independência total, futuramente é possível hospedar a geração localmente.
- A publicação no GitHub Pages pode não ser imediata. Teste no celular e verifique **Settings → Pages** se a URL não carregar.
- Não garanta bloqueio irreversível da tag NFC até confirmar que o endereço `?tag=...` funciona e está corretamente vinculado.
