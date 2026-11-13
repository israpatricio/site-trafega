# Site da Trafega: instruções para qualquer agente de código

Este arquivo vale para qualquer CLI (Claude Code, Codex, Gemini CLI, Cursor, Copilot, OpenCode e outras). O `CLAUDE.md` e o `GEMINI.md` só apontam para cá. Mude as regras aqui, num lugar só.

Este repositório é o site agenciatrafega.com.br, da Trafega, a agência de tráfego pago e presença digital do Israel em Nova Iguaçu (RJ). Tudo fica numa página só (`index.html`), com imagens em `img/` e fontes em `fontes/`. Não tem build: o que está no repositório é o que vai para o ar.

## Onde parou (handoff)

Atualize esta seção sempre que terminar uma sessão de trabalho.

- **13/11/2026:** repositório completo no GitHub (https://github.com/israpatricio/site-trafega), branch `main` em dia com o computador do Israel.
- **Próximo passo:** ligar o site ao repositório seguindo `PUBLICAR-NO-SERVIDOR.md` (uma vez só). Precisa de um navegador com acesso ao Portainer, logado pelo próprio Israel.
- **Pendente:** trocar a foto do farol (`img/farol.webp`), que é provisória e sem licença confirmada.
- O site no ar hoje é a versão publicada em 13/11 às 19h51, igual a este repositório.

## Como o site chega no ar

- O site roda na VPS da Trafega (Hostinger, Docker Swarm), na stack "site" do Portainer: https://porto.agenciatrafega.com.br
- **Situação em 13/11/2026:** o site no ar ainda NÃO lê este repositório. A página está numa config do Swarm (`site_landing_v3`) e as imagens em configs `site_img_*_v1`. Para ligar o repositório ao site, siga `PUBLICAR-NO-SERVIDOR.md` uma vez.
- Depois de ligado, basta dar push na branch `main`. Um serviço na VPS puxa o repositório a cada minuto.
- Só dê push quando o Israel pedir.

## Regras para mexer no texto

- O Israel aprova texto antes de publicar. Mostre o texto novo e espere o ok.
- Voz: frases curtas, português falado, "você" e "WhatsApp" (nunca "cê" ou "zap"). Sem travessão, sem "não é X, é Y", sem tom de guru, sem promessa de resultado para profissional liberal (advogado, médico etc.).
- Números de cliente só com o que o Israel confirmou. Não expor quanto um cliente investe.
- Evite uma palavra sozinha na última linha: use `&nbsp;` entre as duas últimas palavras quando precisar.
- Confira no computador (1440 px) e no celular (390 px) antes de publicar: nada pode passar da largura da tela.

## Regras de design (pedidas pelo Israel para qualquer site ou peça)

- Azul do kit visual: #2229C8. Rosa #F6C7D9, marinho #141B8F e #0C1046, preto #1A1A1A, fundo #F5F6FA.
- Fontes: Archivo Black (títulos), Alte Haas Grotesk (texto), Sarina (só em destaques pontuais: slogan final, selo "Método Maré", "publicitário").
- Estilo: contorno preto de 1 px, botões em pílula, adesivos; Método Maré em linhas numeradas por letra.
- As 20 regras: 1) tirar selos de enfeite; 2) tirar rótulos redundantes; 3) não estilizar palavras aleatórias; 4) fonte mono só onde precisa; 5) usar um design system; 6) mostrar o produto de verdade; 7) aumentar o recurso principal; 8) agrupar pelo espaçamento; 9) títulos específicos; 10) destacar o CTA; 11) uma cor de destaque; 12) ícones consistentes; 13) tirar firulas; 14) raio interno = raio externo − padding; 15) contraste do texto; 16) quebrar bem as linhas dos títulos; 17) alinhar no olho; 18) números tabulares; 19) estados de carregamento; 20) animar só feedback útil.
- Detalhes completos (imagens, estilo, como o Israel trabalha): `contexto/design.md`.

## Contexto da Trafega (só no computador do Israel)

A pasta `contexto/` não vai para o GitHub (está no `.gitignore`, porque o repositório é público). Ela tem `design.md`, `trafega.md` (preços, clientes, processo comercial), `icp.md` e `metodo-mare.md`. Leia o que for relevante antes de escrever texto ou mexer no design. Nunca copie preços ou dados de cliente que não estejam no site para dentro do `index.html` sem o Israel pedir.

Se a pasta `contexto/` não existir (outro computador ou clone novo), trabalhe só com este arquivo e avise o Israel.

## Partes da página que não são texto

- No fim do `index.html` tem um script com o mar em linhas animadas (canvas `data-mare`), o acordeão das objeções, o carregamento dos botões, o evento Contact do pixel no clique do WhatsApp e o repasse de UTM para os links da análise. Não mexa sem necessidade.
- Pixel da Meta: 1196971275764083 (no `<head>`).
- Os links da análise grátis vão para https://analise.agenciatrafega.com.br com `utm_content` de cada botão (topo, hero, metodo, analise, preco, final).

## Créditos e pendências

- Céu da chamada final: Tatiana Reusche (Unsplash). Foto do farol (`img/farol.webp`) é provisória e sem licença confirmada: trocar por uma com licença livre e reaplicar o efeito de tela antiga.
- Histórico de decisões do site: doc "claude/site-v2-publicacao.md" no projeto "Trafega Geral" do claude.ai.
