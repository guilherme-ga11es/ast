# AST12 — Respostas do diagnóstico (Parte 2)

**Qual foi a mensagem exata de erro que o Pytest imprimiu?**

```
E       AssertionError: assert {'resultado': 2} == {'resultado': 8}
E         Differing items:
E         {'resultado': 2} != {'resultado': 8}
FAILED test_main.py::test_somar - AssertionError: assert {'resultado': 2} == ...
========================= 1 failed, 1 passed =========================
```

**O que ele esperava receber e o que recebeu de fato?**

O teste `test_somar` chama `/somar/5/3` e espera `{"resultado": 8}` (5 + 3).
Com o bug (`a - b`), a API devolveu `{"resultado": 2}` (5 - 3). O `test_read_root`
continuou passando: só o teste que cobre a soma detectou o problema.

**O que o CI mostrou?** Que o erro foi barrado antes de chegar à produção: o job
`verificar-api` ficou vermelho (❌) no passo "Rodar Testes".
