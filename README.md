# PHD Healthtec

Site institucional estático. HTML, CSS e JavaScript puros, sem build e sem dependências.

## Estrutura

```
.
├── index.html              Página principal
├── avaliacao.html          Formulário de avaliação confidencial (2 etapas)
├── agendamento.html        Agendador de horário (calendário próprio)
├── ciencia-respaldo.html   Literatura científica de referência
├── assets/                 Logos e imagens (.webp e .png)
└── .nojekyll               Evita o processamento Jekyll no GitHub Pages
```

## Como publicar no GitHub Pages

1. Crie um repositório e envie estes arquivos na raiz.
2. Em **Settings → Pages**, selecione a branch `main` e a pasta `/ (root)`.
3. O site fica disponível em `https://SEU-USUARIO.github.io/SEU-REPO/`.

Para domínio próprio, adicione um arquivo `CNAME` na raiz com o domínio.

## Rodando localmente

Abrir `index.html` direto no navegador funciona. Para simular o servidor:

```bash
python3 -m http.server 8080
```

Depois acesse `http://localhost:8080`.

---

## Pendências antes de publicar

Itens que dependem de decisão ou de dados que ainda não existem.

### 1. Grafia da marca
O conteúdo usa **Healthtec**. O arquivo de logotipo diz **Healthtech**.
Definir qual é a forma oficial e unificar nos dois lugares.

### 2. Número de WhatsApp
Procurar por `5500000000000` e substituir pelo número real.

```bash
grep -rn "5500000000000" *.html
```

### 3. Dados institucionais
Em `index.html`, no rodapé: CNPJ, e-mail de contato e nome do responsável
técnico com CRM estão como espaço reservado.

### 4. Destino do formulário
Em `avaliacao.html`, o formulário tem `data-endpoint=""`. Sem endereço,
a tela de sucesso aparece mas nada é enviado. Preencher com a URL do
backend, Zapier, Make ou Formspree.

> O formulário coleta dado pessoal sob a LGPD. Usar destino próprio, nunca
> planilha pública, e não encaminhar automaticamente para WhatsApp.

### 5. Agenda de horários
Em `agendamento.html`, o objeto `AGENDA` no fim do arquivo define dias,
horários, antecedência e janela. A disponibilidade é gerada por regra, não
lida de uma agenda real, então **dois visitantes podem marcar o mesmo
horário**. Para evitar, preencher `AGENDA.endpoint` com um backend que crie
o evento e devolva os horários ocupados.

### 6. Parceiros clínicos
Os cinco cards em `index.html` usam rótulos genéricos e imagens de espaço
reservado, com o selo "Foto pendente". Os nomes das redes parceiras só
entram após confirmação formal do parceiro.

### 7. Respaldo científico
As oito referências em `ciencia-respaldo.html` são reais, mas sem DOI nem
número de página. Pedir ao time clínico para conferir e completar.

> Citar literatura ao lado de programas comerciais pode ser lido como
> alegação de eficácia. A página traz um aviso no topo. Revisar com o
> jurídico antes de publicar.

### 8. Imagens
`assets/parceiro-*.webp` são gradientes de espaço reservado. Substituir por
fotografia das unidades, mantendo a proporção 3:2 (900×600).

---

## Sistema de design

### Cores da marca

| Token | Hex | Uso |
|---|---|---|
| Midnight Navy | `#0C233F` | Base institucional, texto |
| Deep Blue | `#314869` | Profundidade |
| Tech Teal | `#2D7387` | Tecnologia, CTA |
| Crystal Aqua | `#C0E9F1` | Luz, reflexo |
| Stem Coral | `#D4816A` | Vitalidade, destaque |
| Soft Peach | `#F1CCBE` | Luminosidade |
| Silver Gray | `#C7C7CA` | Neutro |
| Pure White | `#FFFFFF` | Fundo |

Proporção de uso: 60% azul, 25% teal e aqua, 15% coral e peach.

### Tons vivos derivados

`--t-cyan #3FA9C4` · `--t-sky #62C0DA` · `--t-mint #4FC9A8` · `--t-violet #6E7FE8`

Cada tom tem uma variante escurecida (`--t-*-ink`) usada em texto sobre fundo
claro. Os tons vivos ficam em preenchimentos, bordas, ícones e gradientes.
Trocar um pelo outro quebra o contraste mínimo.

### Tipografia

Inter variável com eixo óptico. `opsz 32` nos títulos (corte Display),
`opsz 16` no corpo (corte Text). Carregada do Google Fonts.

### Acessibilidade

Todo texto foi medido nos pixels renderizados e atinge no mínimo 4,5:1.
Todo movimento respeita `prefers-reduced-motion`.

Ao trocar cor de texto ou fundo, medir de novo.
