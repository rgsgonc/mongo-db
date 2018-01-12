# mongo-db

Instalar Mongo
https://www.digitalocean.com/community/tutorials/como-instalar-o-mongodb-no-ubuntu-16-04-pt

Tutorial CRUD
http://www.luiztools.com.br/post/tutorial-crud-em-node-js-com-driver-nativo-do-mongodb/

IDE do banco Mongo
https://studio3t.com/whats-new/install-mongochef-mongodb-linux/

```
// lista os bancos de dados existentes.
show dbs;

// procura por um banco com esse nome, caso não encontre,
// prepara a estrutura necessária para criar um, porém,
// o banco ainda não será criado. No MongoDB um banco
// só existe quando dentro dele existe coleções.
use curso_mongodb;

// excluir o banco de dados a que se está conectado.
db.dropDatabase();

// cria uma coleção dentro do banco de dados.
db.createCollection("alunos");

// lista as coleções de um banco de dados.
db.getCollectionNames();

// excluir uma coleção.
db.cursos.drop();

// insere um documento na coleção.
db.alunos.save({nome: "Fabio"});

// retorna o último documento inserido na coleção.
db.alunos.findOne();

// retorna todos os documentos da coleção.
// a função pretty formata o json para deixá-lo mais legível.
db.alunos.find();
db.alunos.find().pretty();

// tabela de operadores de comparação
SQL			OPERADOR		NOME						OPERAÇÃO
 =			  $eq			Equals						É igual a
 >			  $gt			Greater Than				É maior que
 >=			  $gte			Greater Than or Equal		É maior ou igual a
 <			  $lt			Less Than					É menor que
 <=			  $ltr			Less Than or Equal			É menor ou igual a
!=/<>		  $ne			Not Equal					É diferente de

// retorna os documentos cuja chave nome seja igual a "Fabio".
db.alunos.find({nome:{$eq: "Fabio"}});

// retorna os documentos cuja chave idade seja menor que 30.
db.alunos.find({idade:{$lt: 30}});

// retorna os documentos cuja chave idade seja menor ou igual a 30.
db.alunos.find({idade:{$lte: 30}});

// retorna os documentos cuja chave idade seja maior que 30.
db.alunos.find({idade:{$gt: 30}});

// retorna os documentos cuja chave idade seja maior ou igual a 30.
db.alunos.find({idade:{$gte: 30}});

// retorna os documentos cuja chave sexo seja diferente de "F".
db.alunos.find({sexo:{$ne: "F"}});

// retorna os documentos cuja chave sexo deja diferente de "F"
// e chave idade seja maior que 28.
db.alunos.find({sexo:{$ne: "F"}, idade:{$gt: 28}});

// retorna os documentos cuja chave nome seja igual a "Fabio"
// ou chave idade seja maior ou igual a 28.
db.alunos.find({ 
	$or : [
		{ nome: {$eq: "Fabio"} },
		{ idade: {$gt: 28} }
	]
});

// na função save, caso seja passado o campo identificador _id, o mongo
// substitui o documento no banco, caso ele exista. Caso não exista, o
// documento é simplesmente inserido.
save();

// a função update espera três parâmetros.
// no primeiro parâmetro é passado as condições para o update executar.
// no segundo passamos os campos e valores que sofrerão atualização.
// o terceiro parâmetro é o multi, que por default é false e é opcinal. 
// Caso seja false apenas o primeiro documento sofrerá atualização, 
// mesmo que mais documentos atendam a condição passada.
update({},{}, <optional: {multi:false}>);

// atualiza o documento cujo chave nome seja igual a "Fábio" para "Joãozinho"
// mesmo que haja mais documentos com essa condição, apenas o primeiro sofrerá
// alteração, pois o terceiro parâmetro multi não está sendo passado.
db.alunos.update ( { nome: "Fabio"}, { $set: { nome: "Joãzinho"}} );

// atualiza a chave sexo para "Masculino" de todos os documentos.
// neste caso não foi passado o parâmetro de condição.
db.alunos.update ({}, { $set: { sexo: "Masculino"}}, {multi: true} );

// a função remove espera dois parâmetros.
// o primeiro parâmetro é a condição para que o remove seja executado.
// o segundo parâmetro é do tipo boolean e é opcional, também conhecido
// como justone. Por padrão caso seja omitido é false.
// caso seja passado o valor true ou 1, será removido apenas o primeiro documento.
// caso seja passado o valor false ou 0, será removido todos os documentos
// que satisfaçam a condição.
remove({}, <optional: boolean>);

// remove o primeiro documento cuja chave nome seja igual a "Fabio".
db.alunos.remove({ nome: "Fabio" }, true );

// remove os documentos cuja chave idade seja maior ou igual a 28.
db.alunos.remove({ idade: {$gte: 28} } );

```

