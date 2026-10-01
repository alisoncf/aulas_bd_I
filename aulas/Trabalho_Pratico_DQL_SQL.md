
# Trabalho Prático — DQL em SQL

**Disciplina:** Banco de Dados  
**Conteúdo:** DQL — Data Query Language  
**SGBD:** MariaDB

## Orientações

Crie os banco utilizando os scrtips populados (biblioteca e clínica).

Resolva os exercícios utilizando comandos de consulta SQL (DQL).

Neste trabalho serão utilizados os bancos de dados **biblioteca** e **clinica**.

**Conteúdos trabalhados:**
- SELECT
- WHERE
- Operadores relacionais e lógicos
- LIKE
- IN
- BETWEEN
- ORDER BY
- DISTINCT
- INNER JOIN
- JOIN envolvendo duas ou mais tabelas

**Observação:** neste trabalho ainda **não serão utilizadas funções de agregação**, como `COUNT`, `SUM`, `AVG`, `MAX` e `MIN`, nem `GROUP BY` ou `HAVING`.

Nos exercícios iniciais de cada parte, a solução SQL é apresentada como exemplo. Os demais exercícios devem ser resolvidos pelo aluno.

---

# Parte 1 — Consultas básicas — Biblioteca

1. Liste todos os autores.

**Solução:**
```sql
SELECT * FROM autor;
```

2. Liste todos os livros.

3. Liste todos os membros da biblioteca.

4. Liste todas as editoras.

5. Liste todos os exemplares.

6. Liste todos os empréstimos.

7. Liste todos os tipos de membro.

8. Liste apenas o nome e a nacionalidade dos autores.

9. Liste apenas o título e o ano dos livros.

10. Liste a matrícula dos membros e o código do tipo de membro.

---

# Parte 2 — WHERE e operadores — Biblioteca

11. Liste os livros publicados no ano de 1997.

**Solução:**
```sql
SELECT * FROM livro
WHERE ano = 1997;
```

12. Liste os livros publicados depois do ano 2000.

13. Liste os livros publicados antes de 1990.

14. Liste os livros publicados entre 1990 e 2000.

15. Liste os autores cuja nacionalidade seja brasileira.

16. Liste os autores cuja nacionalidade não seja brasileira.

17. Liste os exemplares que estão disponíveis.

18. Liste os exemplares que não estão disponíveis.

19. Liste os empréstimos que ainda não foram devolvidos.

20. Liste os empréstimos que já foram devolvidos.

---

# Parte 3 — LIKE, IN e BETWEEN — Biblioteca

21. Liste os autores cujo nome começa com a letra M.

**Solução:**
```sql
SELECT * FROM autor
WHERE nome LIKE 'M%';
```

22. Liste os autores cujo nome termina com a letra a.

23. Liste os livros cujo título contenha a palavra “amor”.

24. Liste os livros cujo título contenha a palavra “Brasil”.

25. Liste os livros publicados nos anos 1990, 1995, 2000 ou 2005.

26. Liste os livros cujo ano esteja entre 1980 e 2000.

27. Liste os autores cuja nacionalidade seja Brasileira ou Portuguesa.

28. Liste os membros cuja matrícula comece com “2026”.

---

# Parte 4 — ORDER BY — Biblioteca

29. Liste todos os livros em ordem alfabética pelo título.

**Solução:**
```sql
SELECT * FROM livro
ORDER BY titulo;
```

30. Liste todos os livros do mais antigo para o mais recente.

31. Liste todos os livros do mais recente para o mais antigo.

32. Liste os autores em ordem alfabética.

33. Liste os autores em ordem alfabética decrescente.

34. Liste os empréstimos ordenados pela data de retirada, da mais antiga para a mais recente.

---

# Parte 5 — DISTINCT — Biblioteca

35. Liste as nacionalidades existentes entre os autores, sem repetir valores.

**Solução:**
```sql
SELECT DISTINCT nacionalidade
FROM autor;
```

36. Liste os anos de publicação existentes entre os livros, sem repetir valores.

37. Liste os códigos de editoras utilizados pelos livros, sem repetir valores.

---

# Parte 6 — JOIN — Biblioteca

38. Liste o título de cada livro e o nome da respectiva editora.

**Solução:**
```sql
SELECT l.titulo, e.nomeEditora
FROM livro l
INNER JOIN editora e
    ON e.codEditora = l.fkEditora;
```

39. Liste o título dos livros e seus respectivos códigos de editora.

40. Liste os membros e a descrição do seu tipo de membro.

41. Liste os empréstimos e a matrícula do membro responsável.

42. Liste os empréstimos e o código do exemplar emprestado.

43. Liste os exemplares e o título do livro ao qual pertencem.

44. Liste os livros e seus respectivos autores.

45. Liste os autores e os livros escritos por eles.

46. Liste o número do empréstimo, a data de retirada e o título do livro emprestado.

47. Liste o número do empréstimo, a matrícula do membro e o código do exemplar.

---

# Parte 7 — JOIN + filtros — Biblioteca

48. Liste os livros escritos por autores de nacionalidade Brasileira.

**Solução:**
```sql
SELECT l.titulo, a.nome, a.nacionalidade
FROM livro l
INNER JOIN autoria au
    ON au.fkLivro = l.codigo
INNER JOIN autor a
    ON a.codigo = au.fkAutor
WHERE a.nacionalidade = 'Brasileira';
```

49. Liste os livros escritos por autores de nacionalidade Portuguesa.

50. Liste os livros publicados depois de 2000 e suas respectivas editoras.

51. Liste os exemplares disponíveis e o título dos livros correspondentes.

52. Liste os exemplares indisponíveis e o título dos livros correspondentes.

53. Liste os empréstimos ainda não devolvidos e a matrícula do membro.

54. Liste os empréstimos já devolvidos e a matrícula do membro.

55. Liste os membros cujo tipo seja “Aluno”.

56. Liste os membros cujo tipo seja “Professor”.

57. Liste os livros publicados antes de 2000 e seus autores.

58. Liste os empréstimos realizados em setembro de 2026, apresentando o número do empréstimo e a matrícula do membro.

---

# Parte 8 — Consultas básicas — Clínica

59. Liste todos os médicos.

**Solução:**
```sql
SELECT * FROM Medico;
```

60. Liste todas as especialidades.

61. Liste todos os pacientes.

62. Liste todas as consultas.

63. Liste todas as prescrições.

64. Liste apenas o nome e o CRM dos médicos.

65. Liste apenas o nome e o telefone dos pacientes.

66. Liste os diagnósticos registrados nas consultas.

67. Liste as consultas realizadas em setembro de 2026.

68. Liste os pacientes nascidos depois do ano 2000.

69. Liste os médicos cujo nome comece com a letra A.

70. Liste os pacientes cujo nome contenha a letra “a”.

71. Liste as consultas que possuem diagnóstico informado.

72. Liste as consultas que não possuem diagnóstico informado.

---

# Parte 9 — JOIN — Clínica

73. Liste a data da consulta, o diagnóstico e o nome do paciente.

**Solução:**
```sql
SELECT c.Data,
       c.Diagnostico,
       p.nome AS paciente
FROM Consulta c
INNER JOIN Paciente p
    ON p.codigo = c.fkPaciente;
```

74. Liste a data da consulta e o nome do médico responsável.

75. Liste o nome dos pacientes e as datas de suas consultas.

76. Liste o nome dos médicos e as datas das consultas realizadas por eles.

77. Liste o nome do paciente e seu diagnóstico.

78. Liste o nome do médico e o diagnóstico das consultas realizadas por ele.

79. Liste os pacientes que possuem consultas registradas.

80. Liste os médicos que possuem consultas registradas.

81. Liste as consultas e os respectivos pacientes e médicos.

82. Liste as consultas realizadas em setembro de 2026, apresentando o nome do paciente.

---

# Parte 10 — JOIN envolvendo 3 ou mais tabelas — Clínica

83. Liste o nome do paciente, o nome do médico, a data da consulta e o diagnóstico.

**Solução:**
```sql
SELECT p.nome AS paciente,
       m.nome AS medico,
       c.Data,
       c.Diagnostico
FROM Consulta c
INNER JOIN Paciente p
    ON p.codigo = c.fkPaciente
INNER JOIN Medico m
    ON m.codigo = c.fkMedico;
```

84. Liste o nome do paciente, o nome do médico e o telefone do médico.

85. Liste o nome do paciente, a data da consulta e o CRM do médico.

86. Liste o nome do paciente, o diagnóstico e o nome do médico.

87. Liste as consultas realizadas por médicos de determinada especialidade.

88. Liste o nome do médico e suas especialidades.

89. Liste o nome do médico e todas as especialidades às quais ele está associado.

90. Liste o nome do paciente, o médico e as prescrições relacionadas à consulta.

91. Liste a data da consulta, o paciente, o médico e o medicamento prescrito.

92. Liste o paciente, o médico, a data da consulta, o diagnóstico e a dosagem prescrita.

---

# Parte 11 — Desafios

## Biblioteca

93. Liste os livros, seus autores e suas editoras.

94. Liste os empréstimos ainda não devolvidos, apresentando o título do livro e a matrícula do membro.

95. Liste os livros que possuem mais de um autor, sem utilizar funções de agregação.

96. Liste os membros que já realizaram empréstimos.

97. Liste os livros que possuem exemplares disponíveis.

98. Liste os livros que possuem exemplares atualmente indisponíveis.

## Clínica

99. Liste todas as consultas apresentando paciente, médico, especialidade e diagnóstico.

100. Liste todas as prescrições apresentando paciente, médico, medicamento e dosagem.

101. Liste os pacientes que possuem consultas com médicos de determinada especialidade.

102. Liste os médicos e suas especialidades, juntamente com as consultas realizadas por eles.

103. Liste as consultas de setembro de 2026 apresentando paciente, médico e especialidade.

104. Liste as prescrições realizadas em consultas de setembro de 2026, apresentando paciente, médico, medicamento e princípio ativo.

---

# Entrega

Para cada exercício, apresente:

1. O comando SQL utilizado;
2. O resultado obtido no SGBD;
3. Quando necessário, uma breve explicação sobre a consulta.

**Importante:** não é necessário criar novas tabelas para resolver os exercícios. Utilize apenas os bancos de dados e tabelas fornecidos para a atividade.
