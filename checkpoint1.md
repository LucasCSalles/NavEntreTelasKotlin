# Documentação checkpoint 1
### Resumo do projeto 
Esse projeto foi realizado visando o aprendizado didático em Kotlin na navegação entre multiplas telas usando o Jetpack Compose e o Navigation Compose. Nosso projeto utilizou recursos de passagem de parametros (multiplos ou nao), NavController, Scaffold, Innerpadding e boas práticas para nosso primeiro contato com a matéria. 

### Objetivo do checkpoint 
Esse checkpoint foi realizado para avaliar como o aluno se comportará ao se utilizar de um projeto já criado e em andamento para aplicar conceitos dos quais ele não tem conhecimento, fomentando o aprendizado, manutenção do código já produzido, entendimento do conteúdo até o momento e evolução com documentação do que foi realizado. 

### Atividade 1 (Primeiro Commit) - Passagem de parâmetros obrigatórios na tela de Perfil
Esse primeiro commit tem como objetivo o nosso primeiro contato com parametros obrigatórios sendo passados via Navigation Compose, exemplificado pela variavel "nome". No MainActivity começamos alternado a rota que o composable usa: **composable(route = "perfil/{nome}"**, esse bloco faz com que a variavel nome seja incluida na rota obrigatóriamente. Esse valor é extraído via arguments: **val nome: String? = it.arguments?.getString("nome", "Usuário Genérico")** e marcada/passada como parametro não nulo e obrigatório mais abaixo (as exclamações) **nome!!**. No MenuScreen temos a alteração que envia a variavel nome para o MainActivity na linha: **onClick = { navController.navigate("perfil/Fulano de Tal")** onde "Fulano de tal" seria a variavel de nome sendo passada via navigation compose. Caso essa variavel não existisse e se mantesse apenas "perfil/" o código daria erro, uma vez que setamos como parametro obrigatório. Por fim no PerfilScreen adicionamos a variavel no recebimento de parametros no PerfilScreen e adicionamos ela no bloco de texto **text = "PERFIL - $nome"** para que o campo passe a exibir o nome do usuario que foi passado para ela.

### Atividade 2 (Segundo Commit) - Passagem de parâmetros opcionais na tela de Pedidos
Nesse segundo commit nós começamos a ver parametros opcionais na tela de pedidos. A principal alteração começa na tela de pedidos que passa de uma rota simples que era apenas "pedidos" e passa a receber um parametro OPCIONAL (definido pelo argumento "?") chamado "cliente": **route = "pedidos?cliente={cliente}"**  fazendo com que, mesmo que não seja passado esse parametro a rota ainda funcione. Em continuação da rota foi adicionado o bloco **arguments = listOf(navArgument("cliente") {
defaultValue = "Cliente Genérico"** que define que o valor padrão para cliente é "Cliente Genérico" sendo esse valor utilizado caso nenhum valor seja passado. Então na PedidosScreen a variavel cliente é recebida como parametro permitindo que ela fosse utilizada no texto de pedidos: **text = "PEDIDOS - $cliente",** e exibido ao usuário. Não se preocupe com a diferença do commit acima em referente a quem irá passar o valor, nesse commit ainda não adicionamos quem irá ser responsável.


### Atividade 3 (Terçeiro Commit) - Inserindo valor ao parâmetro opcional na tela de Pedidos
Agora sim, continuando a lógica do commit 2 nós adiconaremos a passagem do parametro via query: **onClick = { navController.navigate("pedidos?cliente=Cliente XPTO") }**, no qual o valor de "cliente" é Cliente XPTO" e é recebido pela tela de Pedidos para sua utilização. Exemplo exibido: Pedidos do Cliente XPTO.  


### Atividade 4 (Quarto Commit) - Passagem de múltiplos parâmetros
Nesse quarto e ultimo commit nós aprendems a passar mais de um parametro entre as telas sendo exemplificado pela adição da variavel "idade" em relação ao 1° commit. Sua rota passa a ser **route = "perfil/{nome}/{idade}",** na qual começamos a passar a variavel "idade" em sua rota e que agora temos uma mudança extra, nós começamos a colocar os argumentos passados em forma de lista definindo seus tipos e quais são (declarando) , ou seja, o bloco: arguments = listOf(navArgument("nome") { type = NavType.StringType }, navArgument("idade") { type = NavType.IntType }) faz com que o nome seja definido como String e a idade como Int. O valor passa a ser extraído em **val idade: Int? = it.arguments?.getInt("idade", 0)** e então passado como parametro obrigatório junto ao "nome" em **idade!!** para o PerfilScreen. No PerfilScreen nós recebemos essa variavel e passamos a utiliza-la no texto: **text = "PERFIL - $nome tem $idade anos",** exemplificação: Perfil- Lucas tem 19 anos. Por ultimo nós realizamos a passagem desses parametros na navegação do botão do MenuScreen em **onClick = { navController.navigate("perfil/Fulano de Tal/27") }** fazendo com que o nome Fulano de Tal de idade 27 anos seja recebido pelo PerfilScreen.



