# json-php
Classe PHP para manipuação de arquivos JSON
Autor: Paulo Leonardo da Silva Cassimiro
Licença: MIT

Classe PHP para manipulação de arquivos JSON.
Essa classe pode ser utilizada para criação e consumo de API’s, uma vez que essa classe também ler arquivos externos via URL.

Como funciona essa classe?
A classe ler um arquivo com formato ou extensão JSON e o converte para um array do PHP. A partir dessa conversão, qualquer método utilizado na classe será em cima do array criado. Quando você salvar o array com as alterações, ela fará a conversão novamente de array do PHP para o formato JSON e assim salvará o arquivo. O arquivo pode ser salvo com saída formata com quebras de linhas, ou não, essa última opção é orientada para otimização em espaço de memória. Lembrando que para a leitura e escrita a classe Json presume que o usuário tem permissão para manipulação do diretório, ou seja, permissão para leitura e escrita. 

Exemplo de instanciação da classse:
 
$file =  “produtos.json”;
-----------------------------------------------------------
$json = new Json($file); ou  $json = Json::url($file);
-----------------------------------------------------------
Lendo arquivos de url externas, exemplo com POKEMON API

$file =  “https://pokeapi.co/api/v2/”;

$json = new Json($file); ou  $json = Json::url($file);


Métodos para manipulação do arquivo Json
-----------------------------------------------------------
gets() : array

Retorna o array que foi criado a partir do arquivo Json

Exemplo: $json->gets();
-----------------------------------------------------------
get(string $key) : string | number | array | boolean 

Retorna o valor do índice do array. Uma chave no formato de string com o nome do índice deve ser informado no argumento.

Exemplo: $json->get('idade');
-----------------------------------------------------------
set(string $key, string | number | array | boolean $value) : void 

Cria um novo índice no array
Uma chave no  formato de string com o nome do índice deve ser informado no argumento  e no segundo argumento deve ser informado o valor da chave.

Exemplo: $json->set('email','pauloleonardoxxx12@gmail.com');
-----------------------------------------------------------
del(string $key) : boolean 

Deleta um índice do array. 
Retorna true no caso de sucesso e false no caso de falha.

Exemplo: $json->del('idade');
-----------------------------------------------------------
read(boolean opcional defaut false) : json 

Retorna o array no formato json. 
Você pode passar um argumento com o valor true ou false.
True para formatação com quebra de linha e false para não formatar a saída.

Exemplo: $json->read(); ou $json->read(true);
-----------------------------------------------------------
merge(array $array) : boolean 

Um um novo array ao array atual, ou seja, faz a mesclagem com um novo array.
Retorna true no caso de sucesso e false no caso de falha.

Exemplo: $json->merge(['telefone'=>'21565588']);
-----------------------------------------------------------
replace(array $array) : boolean 

Substitui o array atual por um novo. A troca ou substituição é total.
Retorna true no caso de sucesso e false no caso de falha.

Exemplo: $json->replace(['telefone'=>'21565588']);
-----------------------------------------------------------
save(boolean opcional defaut false) : boolean | bits 

Salva o arquivo. 
Retorna false no caso de falha ou o número de bits que foram salvos no arquivo.

O arqumento é um boolean, true para saída formatada ou false para saída não formatada. 

Exemplo: $json->save(); ou $json->save(true);
-----------------------------------------------------------
OBS: caso o array do json deriva de uma URL externa ao qual não há arquivo vinculado no seu computador. Você deve usar o método "create" e informar o nome do diretório para criar e salvar o arquivo json local.

$local = 'minha-pasta/pokemon.json'

Exemplo: $json->create($local);
-----------------------------------------------------------
Você também pode passar mais dois parâmetros que são opcionais.

string file : nome do arquivo com o seu diretório

boolean output : saída formata ou não.

boolean sob : sobrescrita do arquivo caso exista um arquivo com o mesmo nome no diretório infomado no primeiro parâmetro. 

Exemplo: $json->create('pokemon.json', true, true);
-----------------------------------------------------------
E por último o método delete que deleta um arquivo json local caso ele exista. O retetono dessa função é true no caso de sucesso e false no caso de falha. 

Exemplo: $json->delete('pokemon.json');
-----------------------------------------------------------
