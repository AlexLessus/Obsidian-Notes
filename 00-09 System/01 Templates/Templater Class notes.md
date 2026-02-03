---
materia: "<% tp.file.folder() %>"
fecha: <% tp.date.now("YYYY-MM-DD") %>
tipo: nota_clase
---
# 🏫 <% tp.file.title %>

## 📋 Resumen de la sesión
> [!abstract] Temas de hoy
> <% tp.file.cursor(1) %>

## 📝 Notas detalladas
- 

## 🔗 Conexiones y Tareas
- [ ] Revisar conceptos de [[<% tp.date.now("YYYY-MM-DD", -1, tp.file.creation_date(), "YYYY-MM-DD") %>]] (Clase anterior)
- **Material adicional:** [[ ]]