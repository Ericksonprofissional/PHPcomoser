<h1>Conceitos e boas praticas do PHP composer</h1>
<a href="https://getcomposer.org/">Pagina do composer</a><br>
Apos fazer o download.<br>

<code>
    mv composer.phar /usr/local/bin/composer
    composer --version
</code>

Iniciando o projeto com composer

<code>composer init</code>

<p>Use as seguinte informações:</p>

<ul>
    <li>Package Name: <em>seu-nickname</em>/buscador-cursos</li>
    <li>Description: Projeto que busca cursos no site da alura</li>
    <li>Author: <em>Seu Nome </em></li>
    <li>Minimum Stability: <em>deixa em branco</em></li>
    <li>Package Type: library</li>
    <li>License: <em>deixa em branco</em></li>
</ul>

Buscando pacotes <a href="https://packagist.org/">packagist<a><br>
<h3>The PHP Unit Testing framework.</h3>
<pre>
    <code>
        composer require --dev phpunit/phpunit<br>
        vendor\bin\phpunit --version
    </code>
</pre>
<h2>PSR-4</h2>
<p>
PHP-FIG propõe diversos padrões, interfaces e recomendações - estas chamadas de <a href="https://www.php-fig.org/psr/psr-4/"> PSRs</a>
</p>

Abrir o arquivo composer.json e acrescentar.
<pre>
    <code>
        "autoload" : {
            "psr-4" : {
                "NovoProjeto\\Buscador\\": "src/"
            }
        }
    </code>
</pre>
<p>
Para gerar o arquivo autoload.php execute na linha de comando:
   <code>composer dumpautoload</code>
</p>
<p>
Assim, todas as classes que começarem com o namespace NovoProjeto\\Buscador\\ serão buscadas na pasta "src/" do nosso projeto. 
Com tudo devemos acrescentar todo arquivo PHP <code>require 'vendor/autoload.php';</code>.
</p>

<p>Em ambiente de produção, quando precisarmos instalar as dependências do projeto, bastará executarmos <code>composer install --no-dev</code></p>

<h2>Instalando o PHPCS</h2>

<p>
ma ferramente bastante interessante, que é um projeto bastante antigo, verifica se nosso código está dentro dos padrões.
Acessaremos o <a href="https://github.com/squizlabs/PHP_CodeSniffer">site da ferramenta</a>, onde encontraremos as instruções de instalação com o Composer.
</p>

<code>composer require --dev squizlabs/php_codesniffer</code>

<p>Após o componente ter sido baixado, poderemos executá-lo pela linha de comando para verificarmos se nosso código está dentro de um padrão especificado</p>
<code>vendor\bin\phpcs --standard=PSR12 src\</code>