# checkout-transparente-gerencianet-laravel
Esse é um projeto de checkout transparente de boleto bancário e cartão de crédito da api da gerencianet em PHP Laravel.

Baixe pelo composer a SDK da Gerencianet: composer require gerencianet/gerencianet-sdk-php

ou no seu projeto no arquivo composer.json adicione e depois de adicionar e salvar, no terminal no diretorio raiz do seu site digite composer update: ... "require": { "gerencianet/gerencianet-sdk-php": "4.*" }, ...

Verefique se a versão do seu projeto laravel é compativel com as verções da SDK da Gerencianet. https://github.com/gerencianet/gn-api-sdk-php

Verifique se o banco de dados esta conectado com seu banco do seu projeto no direitorio raiz do seu site no arquivo .env Verificar o nome do DB_DATABASE= se esta igual do nome do banco de do seu projeto Verificar o nome do DB_USERNAME= se esta igual do nome do banco de do seu projeto Verificar a senha do DB_PASSWORD= se esta igual do nome do banco de do seu projeto 
DB_CONNECTION=mysql 
DB_HOST=127.0.0.1 
DB_PORT=3306 
DB_DATABASE=laravel 
DB_USERNAME=root 
DB_PASSWORD=

No arquivo .env também adicione as suas credenciais adquirida la no seu cadastro da gerencianet adquirido dentro da sua conta em API, Minhas Aplicações e clica no nome da sua aplicação. atenção o GN_SANDBOX true é quando voce estiver fazendo transações testes, apartir do momento que voce terminar seu chechout e quiser utilizar para seus cliente fazer compras aterar para GN_SANDBOX=false.
##GerenciaNet
GN_CLIENT_ID=Seu_Client_Id
GN_CLIENT_SECRET=Seu_Client_Secret
GN_SANDBOX=true
GN_TIMEOUT=30

Depois no seu terminal no diretorio raiz do seu site digite para subir os arquivos do banco de dados no seu banco de dados: php artisan migrate

No diretorio resources/views/ tem os arquivos: 
Packages.blade.php -> Tem os pacotes para escolhido pelo usuario e serem comprados. Aqui pode ser pacote produto, em fim, o que estiver vendendo. 
checkout.blade.php -> Essa parte é para o usuario do seu site escolher qual é o método de pagamento que ele ira escolher, aqui no caso Boleto ou Cartão de Crédito. checkoutCard.blade.php -> Essa parte é o formulario para pagar com o Cartão de Crédito 
checkoutBillet.blade.php -> Essa parte é para pagar com o Boleto Bancario.

No diretorio resources/js -> aqui tem o arquvio js do seu projeto sem estar compilado.

No diretorio public/js -> aqui contém os arquivos js compilado e minificado.

No diretorio Raiz do seu site no arquvio webpack.mix.js: esse arquivo contem todos os seus arquvios css e js para compilar do seu resources e colocar uma copia compilada e minificada no arquivo pulic.

No diretorio routes/web.php: Aqui tem todas as rotas do seu projeto, suas URL do site.

No diretorio app/Http/Controllers/ tem os arquivos que contem os codigos do backand so seu checkout transparente: PackageController.php GerencianetController.php

No diretorio app/Models/ tem os arquivos onde fazem ligação de controller do site e o banco de dados e tambem contém relacionamento entre models: Gerencianet.php Package.php User.php
