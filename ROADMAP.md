# Roadmap — Site da Pousada e Hostel da Ilha de São Francisco do Sul

> Objetivo: sair de "não temos site" para um site próprio que **vende reserva direta**, aparece no Google e fica **sincronizado com Booking.com, Airbnb e Hostelworld** sem overbooking.

---

## Visão geral das fases

| Fase | Nome | Resultado | Prazo sugerido | Custo aproximado |
|---|---|---|---|---|
| 0 | Fundação | Site no ar com domínio próprio + WhatsApp | 1 semana | domínio ~R$ 40/ano, hospedagem grátis |
| 1 | Conteúdo real | Fotos, preços e textos de verdade, SEO local | 2 semanas | fotógrafo opcional |
| 2 | Motor de reservas + Channel Manager | Disponibilidade em tempo real e integração com Booking/Airbnb | 3–6 semanas | mensalidade do PMS |
| 3 | Pagamento online | Sinal via Pix/cartão no próprio site | 2 semanas | taxa por transação |
| 4 | Crescimento | Avaliações, multilíngue, e-mail marketing, pacotes | contínuo | — |

---

## Fase 0 — Fundação (colocar no ar)

- [ ] Registrar domínio no **Registro.br** (ex.: `pousadadailha.com.br` ou `hostelilhasfs.com.br`)
- [ ] Hospedar o `index.html` + pasta `fotos/` em **Netlify**, **Vercel** ou **Cloudflare Pages** (todos têm plano grátis e HTTPS automático)
- [ ] Apontar o domínio para a hospedagem (DNS)
- [ ] **Aprovação do dono da pousada** para publicar o site com o nome e os dados dela
- [ ] Conferir o bloco `CONFIG` no fim do `index.html` (já preenchido com os dados públicos):
  - endereço: R. Agronômica, 195 — Ubatuba, São Francisco do Sul – SC, 89240-000
  - `whatsapp` (confirmar se o (47) 99960-8363 é o número atual), `email`, `instagram`
- [ ] Conferir o array `OPCOES` (cama em beliche, cama de casal, quarto inteiro) e colocar os **preços** (`preco: null` mostra "Consulte")
- [ ] Revisar FAQ (horários, pets/crianças, cancelamento) com o dono
- [ ] Criar e-mail profissional (`contato@seudominio.com.br`) — Zoho Mail grátis ou Google Workspace
- [ ] Criar/atualizar o **Perfil da Empresa no Google** (Google Maps) com link para o site

**Como funciona a reserva hoje:** o formulário calcula uma estimativa e abre o WhatsApp com a mensagem pronta (datas, quarto, hóspedes). Simples, sem custo, e já converte.

---

## Fase 1 — Conteúdo real e SEO local

- [ ] Sessão de fotos (luz natural, manhã/fim de tarde): fachada azul, sacada, pátio das portas coloridas, sinuca, parede grafitada, redário, churrasqueira, cada quarto, cozinha, banheiros, caminho até a praia
- [x] Primeiras fotos reais no site (deck, quintal, mural de giz, sinuca, cozinha, café, placas), com placas de carro borradas
- [x] Fotos do quarto, banheiro, fachada, vista aérea, varanda, casa da árvore e mural no site
- [ ] Confirmar com o dono que as fotos tiradas do Google Maps são da casa (fotos postadas por hóspedes precisam de autorização)
- [ ] Foto da fachada vista da rua e do caminho até a praia
- [ ] Ao adicionar fotos, nunca mostrar senha do Wi-Fi, chave Pix ou placas de carro
- [ ] Fotos em **WebP/JPG** (≤ 250 KB cada), com `alt` descritivo
- [ ] Não reaproveitar fotos de Booking/Hostelworld sem confirmar que são do dono
- [x] Mapa do Google embutido (aparece no domínio próprio; na pré-visualização do Claude fica a foto aérea) + botão "Abrir no Google Maps"
- [ ] Pedir ao dono acesso ao Perfil da Empresa no Google para atualizar fotos, horário e o link do site
- [ ] SEO:
  - [ ] `title` e `meta description` com "hostel em São Francisco do Sul", "pousada centro histórico São Francisco do Sul"
  - [ ] Dados estruturados **Schema.org `Hostel` / `LodgingBusiness`** (JSON-LD) com endereço, telefone, faixa de preço, coordenadas
  - [ ] Open Graph (imagem de compartilhamento no WhatsApp/Instagram)
  - [ ] `sitemap.xml` e `robots.txt`
  - [ ] Cadastrar no **Google Search Console**
- [ ] Analytics: **Google Analytics 4** ou **Plausible** + evento de clique no WhatsApp (medir conversão)
- [ ] Página "Política de privacidade" (LGPD) e banner de cookies, se usar analytics
- [ ] Favicon e ícone para iPhone/Android

---

## Fase 2 — Motor de reservas + integração com Booking.com e afins

É aqui que entra a integração com Booking. **Não se integra direto com a API da Booking** (ela só é liberada para empresas de software certificadas). O caminho é usar um **PMS / Channel Manager** que já é parceiro da Booking, Airbnb, Hostelworld e Expedia.

### 2.1 Escolher o sistema

Critérios: suporte a **camas individuais (dorm)**, integração com Booking + Hostelworld + Airbnb, motor de reservas embutível no site, Pix, suporte em português.

| Opção | Pontos fortes | Observação |
|---|---|---|
| **Cloudbeds** | Muito usado por hostels, vende por cama, channel manager forte | Mensalidade em dólar |
| **Little Hotelier (SiteMinder)** | Bom para pousadas pequenas | Menos focado em dorms |
| **Hostaway / Lodgify** | Ótimos com Airbnb | Mais voltados a aluguel por temporada |
| **Opções brasileiras** (ex.: HQBeds, Omnibees, Hospedin, Desbravador) | Suporte em PT-BR, Pix, nota fiscal | Confirmar integração com Hostelworld e venda por cama |

> Pedir demonstração de 2–3 e testar com os quartos reais antes de assinar. Preços e integrações mudam: confirmar direto com cada fornecedor.

### 2.2 Configuração

- [ ] Cadastrar o quarto compartilhado com **camas individuais** (beliches) + cama de casal + opção de quarto inteiro (mesmos nomes do site)
- [ ] Definir tarifas: baixa/alta temporada, feriados, mínimo de noites, Réveillon/Carnaval
- [ ] Conectar canais: Booking.com, Airbnb, Hostelworld (e Expedia se fizer sentido)
- [ ] Ativar **sincronização de inventário** (2 vias) — fim do overbooking
- [ ] Definir **preço direto mais barato** que nas OTAs (ou benefício: café, late checkout) — a Booking cobra ~15% de comissão

### 2.3 Plugar no site

- [ ] Substituir o formulário atual pelo **widget do motor de reservas** do PMS (geralmente um `<script>` ou `<iframe>`), ou
- [ ] Manter o formulário do site e, no botão "Consultar", redirecionar para a URL de reserva do PMS com as datas preenchidas (`?checkin=...&checkout=...&guests=...`)
- [ ] Manter o botão de WhatsApp como alternativa
- [ ] Opcional: buscar preços/disponibilidade via **API do PMS** e mostrar "a partir de R$ X" atualizado nos cards de quarto

### 2.4 Arquitetura alvo

```
            ┌──────────────┐
  Booking ──┤              │
  Airbnb ───┤   PMS /      ├──► Motor de reservas ──► SITE (seudominio.com.br)
  Hostelworld┤ Channel Mgr │                              │
  Expedia ──┤              │◄── Reservas diretas ─────────┘
            └──────┬───────┘
                   │
           Pix / cartão (gateway)
```

---

## Fase 3 — Pagamento online

- [ ] Ativar gateway pelo próprio PMS (preferível) ou **Mercado Pago / Pagar.me / Asaas / Stripe**
- [ ] Cobrar **sinal (ex.: 30%) via Pix** no ato da reserva direta
- [ ] E-mail automático de confirmação + lembrete 3 dias antes com instruções de chegada
- [ ] Política de cancelamento clara e aceita no checkout
- [ ] Emissão de nota fiscal (verificar com contador / integração do PMS)

---

## Fase 4 — Crescimento

- [ ] **Avaliações reais**: widget do Google ou da Booking/Hostelworld no site (nunca escrever depoimentos fictícios)
- [ ] Site em **inglês e espanhol** (muitos argentinos, uruguaios e mochileiros estrangeiros no litoral de SC)
- [ ] Página de **Experiências** com parceiros: escuna na Babitonga, aula de surf, aluguel de bike — com comissão
- [ ] Pacotes: "Réveillon na ilha", "Festa da Tainha", "Semana de surf"
- [ ] Captação de e-mail/WhatsApp para promoções de baixa temporada
- [ ] Blog/guia local ("o que fazer em São Francisco do Sul em 2 dias") para SEO
- [ ] Instagram integrado (feed no site)
- [ ] Programa para nômades digitais (diárias semanais/mensais com mesa de trabalho)

---

## Checklist técnico do site atual (`index.html`)

- [x] Página única, responsiva (celular, tablet, desktop)
- [x] Redesenho com a skill frontend-design: azul da fachada + lousa + sol do logo pintado; títulos em Big Shoulders, texto em Instrument Sans, giz (Caveat) só no mural
- [x] Estética da casa real: paredes azuis, deck e pergolado de madeira, mural de giz, amendoeiras e as placas Alegria/Gratidão/Harmonia/Amor/Paz
- [x] Seções: hero com foto, barra de reserva, a casa, quarto compartilhado, espaços, mural de giz, praias, galeria com lightbox, como chegar, FAQ, CTA, rodapé
- [x] Formulário de reserva → resumo com estimativa → WhatsApp com mensagem pronta
- [x] Botão flutuante de WhatsApp
- [x] Contatos, opções de cama e fotos centralizados em `CONFIG`, `OPCOES`, `FOTO_QUARTO` e `GALERIA` (fácil de editar)
- [x] Sem dependências externas além de Google Fonts
- [ ] Foto do quarto (Fase 1)
- [ ] Schema.org / Open Graph (Fase 1)
- [ ] Motor de reservas do PMS (Fase 2)

---

## Próximos passos imediatos (esta semana)

1. Mostrar o site ao dono e pegar o OK + preços + fotos
2. Definir o domínio e registrar
3. Subir no Netlify/Vercel e conectar o domínio
4. Encaixar as fotos
5. Pedir demonstração de 2 PMS/channel managers
