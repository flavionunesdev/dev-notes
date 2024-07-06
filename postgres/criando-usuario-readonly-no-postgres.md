# 🙍 Criando usuário readonly no postgres

Como exemplo de uso vamos criar um novo usuário **flavio** e liberar acesso somente leitura para o banco de dados **notas\_db**

***

### Criar um novo usuário \[flavio]

{% code overflow="wrap" %}
```plsql
CREATE USER flavio WITH PASSWORD 'minha-senha-segura';
```
{% endcode %}

### **Concedendo acesso para se conectar ao banco \[notas\_db]**

{% code overflow="wrap" %}
```plsql
GRANT CONNECT ON DATABASE notas_db TO flavio;
```
{% endcode %}

### **Concedendo acesso ao schema \[public]**

{% code overflow="wrap" %}
```plsql
GRANT USAGE ON SCHEMA "public" TO flavio;
```
{% endcode %}

### **Concedendo permissão de consultas**

**Para uma tabela específica \[categorias]**

{% code overflow="wrap" %}
```plsql
GRANT SELECT ON categorias TO flavio;
```
{% endcode %}

**Para todas as tabelas de do schema \[public]**

{% code overflow="wrap" %}
```plsql
GRANT SELECT ON ALL TABLES IN SCHEMA "public" TO flavio;
```
{% endcode %}

**Se você deseja conceder acesso à nova tabela automaticamente no futuro, você deve alterar o padrão:**

{% code overflow="wrap" %}
```plsql
ALTER DEFAULT PRIVILEGES IN SCHEMA "public" GRANT SELECT ON TABLES TO flavio;
```
{% endcode %}

### Referências

* [https://tableplus.com/blog/2018/04/postgresql-how-to-create-read-only-user.html](https://tableplus.com/blog/2018/04/postgresql-how-to-create-read-only-user.htmlhttps://tableplus.com/blog/2018/06/postgresql-how-to-create-user.html)
* [https://tableplus.com/blog/2018/06/postgresql-how-to-create-user.html](https://tableplus.com/blog/2018/04/postgresql-how-to-create-read-only-user.htmlhttps://tableplus.com/blog/2018/06/postgresql-how-to-create-user.html)
