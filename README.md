# Projeto: Testes Unitários com Python e IA

Este repositório contém as entregas das aulas práticas envolvendo a criação de testes unitários com PyUnit e o planeamento de testes automatizados com o apoio de Inteligência Artificial.

## Uso de IA para geração de cenários de teste

### Função escolhida

`potencia(a, b)`

### Prompt utilizado

```text
Atue como um professor de Teste de Software.

Tenho a seguinte função Python:

def potencia(a, b):
    return a ** b

Quero criar testes unitários usando unittest.

Liste pelo menos 6 cenários de teste para essa função.

Para cada cenário, informe:
- nome do cenário;
- entrada;
- resultado esperado;
- tipo do cenário: caso normal, caso de borda ou caso de erro.

Não gere código ainda.
```

### Cenários sugeridos pela IA

| ID | Cenário | Entrada | Resultado esperado | Tipo |
| :--- | :--- | :--- | :--- | :--- |
| T01 | Potência com inteiros positivos | `potencia(2, 3)` | `8` | normal |
| T02 | Expoente zero | `potencia(5, 0)` | `1` | borda |
| T03 | Base zero | `potencia(0, 5)` | `0` | borda |
| T04 | Base negativa, expoente par | `potencia(-2, 2)` | `4` | normal |
| T05 | Expoente negativo | `potencia(2, -1)` | `0.5` | normal |
| T06 | Potência de número alto | `potencia(10, 2)` | `100` | normal |

### Análise dos cenários

Os cenários gerados pela IA foram analisados e inteiramente aceitos. Eles cobrem o caso normal convencional (T01 e T06), mas também verificam comportamentos matemáticos importantes, como bases negativas (T04), resultados em decimais gerados por expoentes negativos (T05) e a propriedade de bases e expoentes nulos (T02 e T03). Nenhum precisou ser descartado pois todos acrescentam validade sem criar sobreposições redundantes.

### Código final dos testes

```python
    def test_potencia_com_varios_casos(self):
        """Testa se a função potencia está funcionando corretamente com múltiplos cenários."""
        casos = [
            (2, 3, 8),
            (5, 0, 1),
            (10, 2, 100),
            (2, -1, 0.5),
            (0, 5, 0),
            (-2, 2, 4),
        ]
        for a, b, esperado in casos:
            with self.subTest(a=a, b=b):
                self.assertEqual(potencia(a, b), esperado)
```

### Resultado da execução

```bash
python -m unittest discover
```

Saída obtida:

```bash
----------------------------------------------------------------------
Ran 8 tests in 0.001s

OK
```
