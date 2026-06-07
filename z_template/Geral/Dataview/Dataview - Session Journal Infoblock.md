```dataviewjs
// Propriedades
const propData = "Data";
const propStatus = "Status";
const propJogadores = "Jogadores";
const propResumo = "Resumo";

// Busca páginas com todas as 4 propriedades definidas
const pages = dv.pages().where(p => 
  p[propData] !== undefined && 
  p[propStatus] !== undefined && 
  p[propJogadores] !== undefined && 
  p[propResumo] !== undefined
);

const count = pages.length;

// Exibe tabela
dv.table(
  ["Página", propData, propStatus, propJogadores, propResumo],
  pages.map(p => [
    p.file.link,
    p[propData],
    p[propStatus],   // mostrará ✅ ou ❌
    p[propJogadores],
    p[propResumo]
  ])
);

// Botão para criar nova Sessão
const newNumber = count + 1;
const newFileName = `Sessão ${newNumber}.md`;

const button = dv.el("button", `🎲 Criar "${newFileName}"`);
button.addEventListener("click", async () => {
  const vault = app.vault;
  if (await vault.adapter.exists(newFileName)) {
    dv.span("⚠️ Já existe uma sessão com esse nome!");
    return;
  }
  
  // Conteúdo com Status padrão = ✅
  const content = `---
${propData}: 
${propStatus}: ✅
${propJogadores}: 
${propResumo}: 
---

Sessão gerada automaticamente em ${new Date().toLocaleString()}.  
**Status:** Use ✅ ou ❌.
`;
  
  try {
    await vault.create(newFileName, content);
    dv.span(`✅ Sessão "${newFileName}" criada!`);
    app.workspace.openLinkText(newFileName, "", false);
  } catch (err) {
    dv.span(`❌ Erro: ${err.message}`);
  }
});
```
