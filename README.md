
# 🧠 Fluent API - Resumo Completo

## ✅ O que é Fluent API?

Fluent API é um **estilo de design de código** que permite **encadear chamadas de métodos** de forma fluida, como uma frase natural. O objetivo é melhorar a **legibilidade**, **expressividade** e **configurabilidade** do código.

```js
const query = new QueryBuilder()
  .select("name", "email")
  .from("users")
  .where("active", true)
  .orderBy("name")
  .build();
```

---

## 🛠️ Características

- **Encadeamento de métodos (`return this`)**
- **Mais legível e declarativo**
- **Forte em configurações complexas**
- Pode ser combinado com o **padrão Builder**, mas não se limita a ele.

---

## 📦 Quando usar Fluent API

| Situação                                               | Justificativa                                                   |
|--------------------------------------------------------|------------------------------------------------------------------|
| Muitas opções/configurações                            | Evita objetos grandes ou construtores com muitos parâmetros     |
| DSLs internas (linguagem específica de domínio)        | Ex: regras de negócio, queries, pipelines                       |
| Melhor legibilidade e legato                           | Código parece frases que descrevem a lógica                     |
| Encadeamento de transformações                         | Ex: validações, formatações, manipulação de dados               |

---

## ❌ Quando evitar

| Situação                                               | Motivo                                                          |
|--------------------------------------------------------|------------------------------------------------------------------|
| Lógica muito simples                                   | Pode ser "overkill" (desnecessário)                             |
| Precisa de objetos imutáveis                           | Fluent APIs geralmente mutam `this`                             |
| Alto risco de esquecer etapas obrigatórias             | Ex: não chamar `withClient()` antes do `build()`                |
| Deseja separação clara entre criação e execução        | Fluent API mistura etapas em uma única cadeia fluida            |

---

## 🧰 Exemplos de uso fora do Builder

### ORM / Query Builder
```js
User.query()
  .where("age", ">", 18)
  .where("country", "Brazil")
  .limit(10)
  .get();
```

### Testes
```js
expect(user.age).toBeGreaterThan(18);
expect(response.status).toBe(200);
```

### Pipelines ou Middlewares
```js
pipeline
  .use(validateInput)
  .use(authenticate)
  .use(handleRequest)
  .run(request);
```

### Transformações
```js
new StringFormatter(" Hello world! ")
  .trim()
  .toUpperCase()
  .replace("WORLD", "DEV")
  .value();
```

---

## 💡 Dicas

- Retorne `this` em todos os métodos para permitir encadeamento.
- Combine com validações para garantir que os métodos obrigatórios foram chamados.
- Use com moderação: o foco é legibilidade, não complexidade.

---

## 🔚 Conclusão

Fluent API é uma ferramenta poderosa de design que **torna o código mais descritivo e configurável**, especialmente útil quando há **múltiplas etapas encadeáveis** ou opções opcionais. Pode ser usado com o padrão Builder ou isoladamente em diversas áreas como queries, testes, validações e pipelines.
