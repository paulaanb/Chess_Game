# Chess_Game

Mi dirección para este repositorio es el siguiente: [ Github: https://github.com/paulaanb/Chess_Game]

La primera tarea consiste en escribir un programa que guarde en un fichero la secuencia de tableros de una partida de ajedrez. Partiremos del tablero inicial donde las filas del tablero están separadas por cambios de línea y las columnas por tabuladores.  El programa debe guardar el tablero inicial en un fichero con el nombre que elija el usuario. Después debe preguntar al usuario si quiere hacer un movimiento o terminar la partida. Cada vez que el usuario quiera hacer un nuevo movimiento debe preguntar la fila y la columna de la pieza que quiere mover y la fila y la columna a la que la quiere mover. Tras ello añadirá el tablero resultante al final del fichero anterior.  Además, una vez generado el fichero con los tableros sucesivos de una partida de ajedrez, el programa preguntará por un movimiento y mostrará por pantalla el tablero correspondiente ese movimiento.

El diagrama de flujo que acompaña al código se muestra a continuación:

![Uploading Captura de pantalla 2021-12-10 a las 19.34.48.png…]()

El tablero para esta tarea es:

♜	♞	♝	♛	♚	♝	♞	♜
♟	♟	♟	♟	♟	♟	♟	♟
							
							
							
							
♙	♙	♙	♙	♙	♙	♙	♙
♖	♘	♗	♕	♔	♗	♘	♖


Y su código se muestra a continuación:

`#La primera tarea consiste en escribir un programa que guarde en un fichero la secuencia de tableros de una partida de ajedrez. Partiremos del tablero inicial donde las filas del tablero están separadas por cambios de línea y las columnas por tabuladores.
#El programa debe guardar el tablero inicial en un fichero con el nombre que elija el usuario. Después debe preguntar al usuario si quiere hacer un movimiento o terminar la partida. 
#Cada vez que el usuario quiera hacer un nuevo movimiento debe preguntar la fila y la columna de la pieza que quiere mover y la fila y la columna a la que la quiere mover. Tras ello añadirá el tablero resultante al final del fichero anterior.
#Además, una vez generado el fichero con los tableros sucesivos de una partida de ajedrez, el programa preguntará por un movimiento y mostrará por pantalla el tablero correspondiente ese movimiento.
def chess_game(fichier_name):
    initial_board = '♜\t♞\t♝\t♛\t♚\t♝\t♞\t♜\n♟\t♟\t♟\t♟\t♟\t♟\t♟\t♟\n\t\t\t\t\t\t\t\n\t\t\t\t\t\t\t\n\t\t\t\t\t\t\t\n\t\t\t\t\t\t\t\n♙\t♙\t♙\t♙\t♙\t♙\t♙\t♙\n♖\t♘\t♗\t♕\t♔\t♗\t♘\t♖'
    board = []
    for i in initial_board.split('\n'):
        # Dividimos al tablero la lista que resulta de dividir la subcadena i por el caracter de tabulación.
        board.append(i.split('\t'))
    # Ponemos el archivo en modo lectura y creamos un bucle para recorrer las filas del tablero
    f = open(fichier_name, 'w')
    for i in board:
        f.write('\t'.join(i) + '\n')
    f.close()
    
    movement = 0
    # Creamos un bucle para realizar movimientos en la partida hasta que el usario decida terminar.
    while True:
        continuar = input('¿Desea realizar algún movimiento? (Si/ No):')
        if continuar != 'Si':
            break
        else:
            original_line = int(input('Por favor introduzca la fila de la pieza que desea mover: '))
            original_column = int(input('Por favor introduzca la columna de la pieza que desea mover: '))
            destination_line = int(input('Por favor introduzca la fila a donde desea mover la pieza: '))
            destination_column = int(input('or favor introduzca la columna a donde desea mover la pieza: '))
            board[destination_line-1][destination_column-1] = board[original_line-1][original_column-1]
            board[original_line-1][original_column-1] = ''
            movement += 1
            # Abrimos el archivo en modo añadir y añadimos una cadena con el número de movimientos
            f = open(fichier_name, 'a')
            f.write('Movimiento' + str(movement) + '\n')
            # Creamos un bucle para recorrer las filas del tablero y escribimos cada fila en una linea
            for i in board:
                f.write('\t'.join(i) + '\n')
            f.close()
    return
chess_game('partida1.txt')

#Una vez generado el fichero con los tableros sucesivos de una partida de ajedrez, el programa preguntará por un movimiento y mostrará por pantalla el tablero correspondiente ese movimiento.
def board(fichier_name, n):
    # Ponemos el archivo en modo lectura y dividimos la cadena por el caracter de cambio de línea.
    f = open(fichier_name, 'r')
    boards = f.read().split('\n')
    # Creamos un bucle para imprimir las lineas correspondientes al tablero. Cada tablero empieza siempre en una línea múltiplo de 9.
    for i in boards[n*9:n*9+8]:
        print(i)
    return

board('partida1.txt', 2)´


