# Vida de Gato — landing page da Dra. Eliane Senger

Registro do projeto para uso em novas conversas com o Claude. Estado em 10/11/2026.

## Visão geral

- Landing page de página única da Dra. Eliane Senger, veterinária de gatos (Medicina Felina) com atendimento domiciliar em Joinville/SC.
- Endereço oficial (canônico): https://www.vidadegato.com/
- Idioma do site: português do Brasil.
- Contatos exibidos no site: WhatsApp +55 47 99282-1447, e-mail esr@vidadegato.com, Instagram @elianesenger.

## Stack

- HTML estático em um único arquivo (`index.html`), sem etapa de build.
- Tailwind CSS via CDN (`cdn.tailwindcss.com`), com configuração de cores no próprio HTML.
- Fonte Inter (Google Fonts).
- JavaScript mínimo no fim da página: menu mobile (com `aria-expanded`) e ano atual no rodapé.
- Paleta: `brand-teal` (50 `#e0f2f1` a 900 `#004d40`; 700 `#00796b` é o tom de botões e rodapé) e `brand-orange-500` `#ff7043` (CTA e estrelas).

## Estrutura de pastas

Pasta local: `~/Documents/0-DEV/vidadegato`

| Caminho | Vai para o Git | Conteúdo |
|---|---|---|
| `index.html` | Sim | A página inteira |
| `images/` | Sim | Imagens otimizadas usadas no site |
| `.gitignore` | Sim | Ignora `.DS_Store`, `Eliane/`, `Logo/` |
| `.vercelignore` | Sim | Impede que `CLAUDE.md` seja publicado no site |
| `CLAUDE.md` | Sim | Este registro |
| `Eliane/` | Não | Fotos originais em alta resolução (dezenas de arquivos de 5 a 20 MB) |
| `Logo/` | Não | Logos originais: `Logo Verde.png`, `Logo Branco.png`, selo Cat Friendly |

## Seções da página

| Âncora | Conteúdo |
|---|---|
| `#inicio` | Chamada principal, botão de agendamento e foto da Dra. Eliane com um gato |
| `#servicos` | "Serviços Especializados", 6 cards |
| `#sobre` | Logo Vida de Gato em círculo, texto sobre a Dra. Eliane e selo Cat Friendly |
| `#depoimentos` | "O que os tutores dizem", 9 depoimentos com 5 estrelas |
| `#contato` | CTA para WhatsApp |
| Rodapé | E-mail, WhatsApp, Instagram e ano automático |

### Serviços (ordem atual)

1. Medicina Felina (Clínica)
2. Consulta e Orientação Pediátrica
3. Atendimento Domiciliar
4. Consultoria FIV / FELV / PIF
5. Exames e Vacinas em Casa
6. Consultoria para Veterinários

## Regras de conteúdo

- **Não mencionar Odontologia.** A Dra. Eliane não atende mais essa área. Todo o conteúdo relacionado foi removido, inclusive o depoimento que citava cirurgia dentária.
- Não alterar as palavras de depoimentos de clientes; se um depoimento deixar de servir, remover inteiro.
- Ao mudar serviços ou depoimentos, atualizar também o JSON-LD (`availableService`, `review` e `reviewCount`, hoje 9).
- O JSON-LD não aceita comentários `//`; mantê-lo como JSON válido.

## Imagens

Todas em `images/`, sem metadados, em sRGB, com versão WebP (principal) e JPEG/PNG (reserva), usadas via `<picture>` com `srcset`.

| Arquivo base | Tamanhos | Origem | Uso |
|---|---|---|---|
| `dra-eliane-senger-gato` | 600 e 1200 px (3:2) | `Eliane/Eliane-49.jpg`, recortada e com sombras clareadas | Foto principal em `#inicio` |
| `logo-vida-de-gato` | 300 e 600 px (quadrada) | `Logo/Logo Verde.png`, com margem extra para o recorte circular | Círculo em `#sobre` |
| `selo-cat-friendly-veterinarian` | 200, 400 e 480 px | `Logo/Cat-Friendly-Veterinarian_R_CMYK_2024.png`, só redimensionado | Selo em `#sobre`, exibido com 240 px de largura |

Convenção para novas imagens: nome em minúsculas com hifens e a largura no final; gerar tamanho normal e retina; não alterar a arte do selo Cat Friendly (marca registrada).

## Git e publicação

- Repositório: https://github.com/marcelojulianoramos/vidadegato (branch `main`).
- Vercel: time `marceloramos`, projeto `vidadegato` (`prj_cghnkfhGkmGcv0sBXxc018RrKYuO`), sem framework.
- Todo `git push` na `main` publica automaticamente em produção.
- O Marcelo costuma fazer o commit e o push ele mesmo; o Claude prepara os arquivos e só faz commit ou push quando pedido.
- Convenção de backup usada no início do projeto: cópias em `BKP/` com timestamp no nome, por exemplo `index-V1-20261110-1600.html`. O histórico do Git cumpre esse papel hoje.

### Histórico de commits

| Commit | Descrição |
|---|---|
| `217ea21` | Upload inicial |
| `f85d296` | Correção do HTML, SEO, acessibilidade e desempenho |
| `341a403` | Remoção da Odontologia |
| `4d2f4cb` | "Versão V1": card de Pediatria, foto principal, logo e selo Cat Friendly |

## Domínios

Os três domínios estão registrados na GoDaddy, com DNS na própria GoDaddy, e apontam para o mesmo projeto na Vercel.

| Endereço | Comportamento |
|---|---|
| `www.vidadegato.com` | Exibe o site (endereço oficial) |
| `vidadegato.com` | Redireciona (308) para `www.vidadegato.com` |
| `www.elianesenger.com` | Exibe o site |
| `elianesenger.com` | Redireciona (308) para `www.elianesenger.com` |
| `www.elianesenger.com.br` | Exibe o site |
| `elianesenger.com.br` | Redireciona (308) para `www.elianesenger.com.br` |
| `vidadegato.vercel.app` | Endereço padrão da Vercel |

Os domínios `elianesenger` exibem o mesmo conteúdo; a tag canônica aponta para `www.vidadegato.com`, então não há conteúdo duplicado para o Google.

## DNS padrão (igual nas três zonas, 15 registros cada)

| Tipo | Nome | Valor | Finalidade |
|---|---|---|---|
| A | `@` | `216.198.79.1` | Site (Vercel) |
| CNAME | `www` | `608a39f654f90681.vercel-dns-017.com.` | Site (Vercel) |
| CNAME | `_domainconnect` | `_domainconnect.gd.domaincontrol.com.` | Padrão GoDaddy |
| MX | `@` | `aspmx.l.google.com.` (1), `alt1` e `alt2` (5), `alt3` e `alt4` (10) | E-mail no Google Workspace |
| TXT | `@` | `v=spf1 include:_spf.google.com ~all` | SPF |
| TXT | `google._domainkey` | Chave DKIM própria de cada domínio | DKIM do Google |
| TXT | `_dmarc` | `v=DMARC1; p=none;` | DMARC em modo de observação |
| TXT | `@` | `google-site-verification=...` (código próprio de cada domínio) | Verificação do Google |
| NS / SOA | `@` | Fixos da GoDaddy, diferentes por domínio | — |

Decisões tomadas:

- O e-mail dos três domínios fica só no Google Workspace. Todos os registros do iCloud (MX, DKIM `sig1._domainkey`, `apple-domain`) foram removidos.
- O encaminhamento de domínio da GoDaddy foi desativado nos domínios `elianesenger` (ele criava registros A bloqueados para `15.197.225.128` e `3.33.251.168`).
- No `elianesenger.com.br`, o SPF em duas partes e o DMARC `p=quarantine` criados automaticamente pela GoDaddy foram substituídos pelo padrão acima. Se reaparecerem, desativar o recurso automático da GoDaddy.

## Pendências

- **Favicon:** a página não declara nenhum; criar a partir do logo.
- **Imagem de compartilhamento:** `og:image` e `twitter:image` ainda usam placeholder (`placehold.co`); gerar uma de 1200×630.
- **Texto do selo:** a página diz "Cat Friendly Veterinary Professional" e "AAFP", mas o selo diz "Cat Friendly Veterinarian" e "Feline Veterinary Medical Association". Confirmar o nome correto com a Dra. Eliane.
- **Seção Sobre:** mostra o logo, não uma foto da Dra. Eliane. Trocar se desejado.
- **DKIM:** confirmar no Admin do Google Workspace que a autenticação foi iniciada nos três domínios.
- **DMARC:** após algumas semanas com DKIM ativo, avaliar subir de `p=none` para `p=quarantine`.
- **Desempenho:** o Tailwind via CDN não é recomendado para produção; considerar gerar o CSS final.
