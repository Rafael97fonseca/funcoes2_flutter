Flutter – Row, Column, Stack, Imagens, Texto e ListView
1. Explique o conceito de um widget Row em Flutter

O Row é um widget que organiza seus widgets filhos horizontalmente, ou seja, em uma única linha.

Exemplo:
Row(
  children: [
    Icon(Icons.home),
    Text('Início'),
    Icon(Icons.settings),
  ],
)

Resultado:

🏠 Início ⚙️
Principais características:
Organiza widgets da esquerda para a direita.
Pode conter qualquer tipo de widget.
Permite controlar alinhamento e espaçamento.
2. Como posso adicionar espaçamento uniforme entre os widgets em um Row?
Método 1: MainAxisAlignment.spaceEvenly
Row(
  mainAxisAlignment: MainAxisAlignment.spaceEvenly,
  children: [
    Icon(Icons.home),
    Icon(Icons.favorite),
    Icon(Icons.settings),
  ],
)

Distribui os widgets igualmente em toda a linha.

Método 2: SizedBox
Row(
  children: [
    Icon(Icons.home),
    SizedBox(width: 20),
    Icon(Icons.favorite),
    SizedBox(width: 20),
    Icon(Icons.settings),
  ],
)

Cria um espaço fixo entre os elementos.

3. Qual a diferença entre MainAxisAlignment e CrossAxisAlignment em um Row?

Em um Row:

Main Axis = Horizontal
Cross Axis = Vertical
MainAxisAlignment

Controla o alinhamento horizontal.

Row(
  mainAxisAlignment: MainAxisAlignment.center,
  children: [...]
)

Opções:

MainAxisAlignment.start
MainAxisAlignment.center
MainAxisAlignment.end
MainAxisAlignment.spaceBetween
MainAxisAlignment.spaceAround
MainAxisAlignment.spaceEvenly
CrossAxisAlignment

Controla o alinhamento vertical.

Row(
  crossAxisAlignment: CrossAxisAlignment.center,
  children: [...]
)

Opções:

CrossAxisAlignment.start
CrossAxisAlignment.center
CrossAxisAlignment.end
CrossAxisAlignment.stretch
4. Explique o conceito de um widget Column em Flutter

O Column organiza widgets verticalmente.

Exemplo:
Column(
  children: [
    Text('Nome'),
    Text('Email'),
    Text('Telefone'),
  ],
)

Resultado:

Nome
Email
Telefone
Características:
Organiza widgets de cima para baixo.
Equivalente vertical do Row.
Muito usado em formulários e telas.
5. Qual a diferença entre MainAxisAlignment e CrossAxisAlignment em um Column?

Em um Column:

Main Axis = Vertical
Cross Axis = Horizontal
MainAxisAlignment

Controla o alinhamento vertical.

Column(
  mainAxisAlignment: MainAxisAlignment.center,
  children: [...]
)
CrossAxisAlignment

Controla o alinhamento horizontal.

Column(
  crossAxisAlignment: CrossAxisAlignment.start,
  children: [...]
)
6. Explique o conceito de um widget Stack em Flutter

O Stack permite empilhar widgets uns sobre os outros.

Semelhante às camadas de um editor de imagens.

Exemplo:
Stack(
  children: [
    Container(
      width: 200,
      height: 200,
      color: Colors.blue,
    ),
    Text('Olá'),
  ],
)

O texto será exibido sobre o Container.

7. Quais as vantagens de usar Stack em vez de Row ou Column?
Row e Column

Organizam widgets sequencialmente.

A B C

ou

A
B
C
Stack

Permite sobreposição.

---------
|   B   |
| A   C |
---------
Casos de uso:
Texto sobre imagem
Botão flutuante
Badges de notificações
Sobreposição de elementos
8. Como posso posicionar widgets específicos dentro de um Stack?

Utilizando o widget Positioned.

Exemplo:
Stack(
  children: [
    Container(
      width: 300,
      height: 300,
      color: Colors.blue,
    ),

    Positioned(
      top: 20,
      left: 20,
      child: Text('Topo'),
    ),

    Positioned(
      bottom: 20,
      right: 20,
      child: Text('Base'),
    ),
  ],
)

Propriedades:

top
bottom
left
right
9. Como posso exibir uma imagem de um arquivo local em Flutter?
Passo 1

Criar pasta:

assets/images/
Passo 2

Adicionar imagem.

assets/images/logo.png
Passo 3

Configurar no pubspec.yaml

flutter:
  assets:
    - assets/images/
Passo 4

Exibir imagem.

Image.asset(
  'assets/images/logo.png',
)
10. Quais propriedades posso usar para controlar a aparência do texto?

Utilizando TextStyle.

Exemplo
Text(
  'Flutter',
  style: TextStyle(
    fontSize: 24,
    color: Colors.blue,
    fontWeight: FontWeight.bold,
    fontStyle: FontStyle.italic,
  ),
)
Principais propriedades
fontSize
color
fontWeight
fontStyle
fontFamily
letterSpacing
wordSpacing
height
decoration
11. Como posso exibir um texto em várias linhas?
Text(
  'Flutter é um framework desenvolvido pela Google para criar aplicações multiplataforma.',
)

O Flutter quebra as linhas automaticamente.

Limitar linhas
Text(
  'Texto longo...',
  maxLines: 3,
)
Reticências
Text(
  'Texto muito longo...',
  maxLines: 2,
  overflow: TextOverflow.ellipsis,
)

Resultado:

Texto muito...
12. Como posso criar uma lista de rolagem vertical em Flutter?

Utilizando ListView.

ListView(
  children: [
    Text('Item 1'),
    Text('Item 2'),
    Text('Item 3'),
  ],
)

A rolagem vertical é automática.

13. Como posso adicionar itens dinamicamente a um ListView?

Utilizando uma lista e o ListView.builder.

List<String> nomes = [
  'João',
  'Maria',
  'Pedro'
];
ListView.builder(
  itemCount: nomes.length,
  itemBuilder: (context, index) {
    return ListTile(
      title: Text(nomes[index]),
    );
  },
)

Ideal para listas grandes.

14. Quais as diferenças entre ListView.builder e ListView.separated?
ListView.builder

Cria apenas os itens.

ListView.builder(
  itemCount: 100,
  itemBuilder: (context, index) {
    return Text('Item $index');
  },
)
ListView.separated

Cria itens e separadores.

ListView.separated(
  itemCount: 100,
  itemBuilder: (context, index) {
    return Text('Item $index');
  },
  separatorBuilder: (context, index) {
    return Divider();
  },
)

Resultado:

Item 1
---------
Item 2
---------
Item 3
15. Como posso usar ListTile para criar itens de lista em um ListView?
ListView(
  children: [
    ListTile(
      title: Text('João'),
      subtitle: Text('Aluno'),
    ),
    ListTile(
      title: Text('Maria'),
      subtitle: Text('Professora'),
    ),
  ],
)
16. Como posso tornar os itens ListTile interativos (clicáveis)?

Utilizando onTap.

ListTile(
  title: Text('Clique aqui'),
  onTap: () {
    print('Item clicado');
  },
)

Também existe:

onLongPress

Para clique longo.

17. Quais as vantagens de usar ListTile em vez de widgets de texto simples?
Text
Text('João')

Exibe apenas texto.

ListTile
ListTile(
  leading: Icon(Icons.person),
  title: Text('João'),
  subtitle: Text('Aluno'),
)

Possui:

Ícones
Título
Subtítulo
Eventos de clique
Melhor aparência visual
Layout pronto para listas
18. Como os widgets são organizados dentro de um Stack?

Os widgets são organizados em camadas.

Exemplo
Stack(
  children: [
    Container(color: Colors.blue),
    Image.asset('imagem.png'),
    Text('Texto'),
  ],
)

Ordem:

Camada 1 → Container
Camada 2 → Imagem
Camada 3 → Texto

O último widget fica sobre os anteriores.

19. Como posso exibir uma imagem da internet em Flutter?

Utilizando Image.network.

Image.network(
  'https://picsum.photos/300',
)

Também pode definir tamanho:

Image.network(
  'https://picsum.photos/300',
  width: 300,
  height: 200,
)
20. Como posso adicionar um efeito de desvanecimento a uma imagem?

Uma forma simples é usar Opacity.

Opacity(
  opacity: 0.5,
  child: Image.asset(
    'assets/images/foto.jpg',
  ),
)

Valores:

0.0 → invisível
0.5 → semi-transparente
1.0 → totalmente visível
FadeInImage

Para carregar imagem da internet com efeito de fade.

FadeInImage.assetNetwork(
  placeholder: 'assets/loading.gif',
  image: 'https://picsum.photos/300',
)
21. Como posso adicionar ícones e outros elementos visuais a um ListTile?
leading

Elemento à esquerda.

leading: Icon(Icons.person)
trailing

Elemento à direita.

trailing: Icon(Icons.arrow_forward)
Exemplo completo
ListTile(
  leading: CircleAvatar(
    child: Icon(Icons.person),
  ),
  title: Text('Rafael'),
  subtitle: Text('Desenvolvedor Flutter'),
  trailing: Icon(Icons.arrow_forward_ios),
  onTap: () {
    print('Clicou');
  },
)

Resultado:

[👤] Rafael
     Desenvolvedor Flutter              >
Resumo para prova
Widget	Função
Row	Organiza widgets horizontalmente
Column	Organiza widgets verticalmente
Stack	Empilha widgets
Image.asset	Exibe imagem local
Image.network	Exibe imagem da internet
ListView	Lista com rolagem
ListView.builder	Lista dinâmica
ListView.separated	Lista com separadores
ListTile	Item de lista pronto
Positioned	Posiciona widgets dentro do Stack
Opacity	Controla transparência
TextStyle	Personaliza textos