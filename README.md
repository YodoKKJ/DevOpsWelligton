# Bistrô Sabor da Vila

Sistema didático de comandas e cadastro de produtos feito em PHP e MariaDB/MySQL.

## Rodar no Windows com XAMPP

1. Instale o [XAMPP](https://www.apachefriends.org/download.html) com Apache, MySQL e PHP.
2. Coloque os arquivos deste repositório em uma pasta chamada `bistro_devops` dentro de `htdocs`. Exemplos:
   - Instalação padrão: `C:\xampp\htdocs\bistro_devops`
   - Instalação usada neste PC: `D:\XAMMP\htdocs\bistro_devops`

   O arquivo `index.php` deve ficar diretamente dentro de `bistro_devops`.
3. Abra o painel do XAMPP e clique em **Start** para **Apache** e **MySQL**.
4. Acesse [phpMyAdmin](http://localhost/phpmyadmin/), escolha **Importar**, selecione [`database.sql`](database.sql) e execute. O script cria o banco `bistro_devops`, as tabelas e 10 produtos de exemplo. **Importe uma vez só:** uma segunda importação duplica os produtos de exemplo.
5. Confira [`config/database.php`](config/database.php). A configuração inicial usa `localhost`, banco `bistro_devops`, usuário `root` e senha vazia, que é o padrão de uma instalação local do XAMPP. Se a sua instalação usa outra senha, ajuste esse arquivo localmente. Não envie credenciais reais ao GitHub.
6. Abra o [painel de comandas](http://localhost/bistro_devops/) e a [página de produtos](http://localhost/bistro_devops/produtos.php).

O projeto exige a extensão `pdo_mysql` do PHP, incluída na instalação padrão do XAMPP.

### Se preferir importar pelo terminal

No PowerShell, use o cliente MySQL do XAMPP com UTF-8. Ajuste os caminhos se o XAMPP estiver em outro local:

```powershell
& 'D:\XAMMP\mysql\bin\mysql.exe' -u root --default-character-set=utf8mb4 -e "source D:/XAMMP/htdocs/bistro_devops/database.sql"
```

O arquivo SQL contém `SET NAMES utf8mb4` para preservar acentos como `Porção` e `Água`.

## Problemas comuns

- **A página não abre:** confira se o Apache está ativo e se a pasta está em `htdocs\bistro_devops`.
- **Erro de conexão com o banco:** inicie o MySQL, importe `database.sql` e confira usuário e senha em `config/database.php`.
- **Porta 80 ocupada:** libere a porta ou ajuste a porta do Apache no XAMPP e use essa porta no endereço, por exemplo `http://localhost:8080/bistro_devops/`.
- **Nomes com caracteres estranhos:** confira a codificação UTF-8 na importação. Se os dados já estiverem corrompidos, uma nova importação sem limpar os produtos cria duplicatas.

O projeto não possui login. Use dados de demonstração e mantenha a aplicação restrita ao ambiente local até implementar autenticação e autorização.
