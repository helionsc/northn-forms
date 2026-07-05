# Northn Forms — Construtor de Formulários

Ferramenta para montar formulários personalizados sem mexer em código: cores, logo,
textos e perguntas (com tipos diferentes, incluindo múltipla escolha) tudo configurável
visualmente, com pré-visualização ao vivo animada.

**Importante:** isso é independente do formulário que já está em produção (o da Abrace).
Nada foi publicado nem alterado lá — este é um projeto novo, só pra você revisar.

## Como usar

1. Abra o arquivo `construtor.html` no navegador (funciona local, sem precisar de servidor).
2. No painel da esquerda, configure:
   - **Marca**: cor principal, cor secundária, emoji/ícone e nome da organização.
   - **Textos**: título, descrição de boas-vindas, texto do botão e mensagem de sucesso.
   - **Perguntas**: adicione quantas quiser, escolha o tipo (texto, e-mail, telefone,
     texto longo, múltipla escolha, caixas de seleção ou lista suspensa), marque se é
     obrigatória, e informe as opções (uma por linha) quando o tipo pedir.
3. A pré-visualização à direita atualiza em tempo real, exatamente como o formulário
   final vai ficar.
4. Quando estiver pronto, clique em **"Baixar formulário (HTML)"** — isso gera um
   arquivo `.html` único, pronto pra publicar em qualquer lugar (Vercel, GitHub Pages,
   ou até anexado num e-mail).

## Envio das respostas

Sem configurar nada, o formulário mostra a mensagem de sucesso mas **não envia os
dados pra lugar nenhum** — configure pelo menos uma opção antes de usar de verdade:

- **Webhook URL**: qualquer endpoint que aceite POST em JSON (Zapier, Make, uma Edge
  Function do Supabase, etc.). Recebe `{ respostas, resumo, data, hora }`.
- **EmailJS**: mesma ferramenta já usada no formulário da Abrace. Preencha Public Key,
  Service ID e Template ID. No template do EmailJS, use as variáveis `{{resumo}}`,
  `{{data}}` e `{{hora}}` pra exibir todas as respostas formatadas.

Pode usar os dois ao mesmo tempo, se quiser.

## Limitações desta primeira versão

- Sem lógica condicional (perguntas que mudam conforme a resposta anterior).
- Sem upload de imagem de logo (só emoji/ícone em texto) — dá pra evoluir depois.
- Sem armazenamento de respostas dentro do próprio formulário — depende do Webhook
  ou EmailJS configurado.

Essas ficam como próximos passos, se fizer sentido evoluir isso pra um produto
completo (Northn Forms) mais pra frente.
