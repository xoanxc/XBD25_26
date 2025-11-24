<%*
const enunciado = await tp.system.prompt("Enunciado do exercicio");
const consulta = await tp.system.prompt("Consulta SQL");
const resultado = await tp.system.prompt("Resultado esperado");
-%>

## 📝 Enunciado
<%= enunciado %>

---

## 🔍 Consulta SQL
```sql
<%= consulta %>
```

---

## 📊 Resultado esperado
```
<%= resultado %>
```

---

## 🗂 Notas adicionais (opcional)
-  
