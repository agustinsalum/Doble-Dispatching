# Doble-Dispatching
Tecnica Objetos

Ayudante diplomada: Gabriela Perez

Para decidir como tengo que hacer algo, debo conocer a que clase pertenece el objeto que recibe el mensaje, pero tambien a que clase pertenece el parametro. El ejemplo tipico es la suma entre enteros e imaginarios. Otro que recien mire en internet y me parece mas piola es el juego de piedra papel y tijera.
Para saber el resultado debo conocer los dos movimientos
Tijera>> jugarCon: otroMovimiento
Piedra>>jugarCon: otroMovimiento
Papel>>jugarCon: otroMovimiento

Como hago? aca viene lo del doble dispatching. No lo puedo resolver, pero puedo hacer un dispatching del mensaje diciendole en el nombre del mensaje algo que le sugiera quien soy (o le digo quien soy, asi sabe como resolver el final)-

Tijera>> jugarCon: otroMovimiento
      otroMovimiento jugadaConTijera
Piedra>>jugarCon: otroMovimiento
      otroMovimiento jugadaConPiedra
Papel>>jugarCon: otroMovimiento
      otroMovimiento jugadaConPapel

Asi cuando recibe la segunda parte del mensaje, ya vamos a saber que hacer
Tijera >> jugadaConTijera
   ^empate
Piedra>> jugadaConTijera
  ^ gano
Papel>> jugadaConTijera
^ pierdo

Tijera >> jugadaConPiedra
   ^pierdo
Piedra>>  jugadaConPiedra
  ^ empate
Papel>>  jugadaConPiedra
^ gano

Tijera >> jugadaConPapel
   ^gano
Piedra>>  jugadaConPapel
  ^ pierdo
Papel>>  jugadaConPapel
^ empate

Si no lo notaste, los mensajes crecen en cantidad. Lo bueno es que si aparece un nuevo tipo de jugada, esas van a SEGUIR FUNCIONANDO. Habra que agregar en cada clase
Tijera >> jugadaConNuevo
Piedra >> jugadaConNuevo
Papel >> jugadaConNuevo

Y en la clase nueva los mensajes correspondientes.
Nuevo>>jugarCon: otroMovimiento
