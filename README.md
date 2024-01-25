board = list(range(1, 10))
win_position = [(1, 2, 3), (4, 5, 6), (7, 8, 9), (1, 4, 7), (2, 5, 8), (3, 6, 9), (1, 5, 9), (3, 5, 7)]


def draft_board():
    print("-------------")
    for i in range(3):
        print("|", board[0 + i * 3], "|", board[1 + i * 3], "|", board[2 + i * 3], "|")
    print("-------------")


def take_input(n):
    while True:
        value = input("куда поставить:" + n)
        if not (value in "123456789"):
            print("ошибочный ввод, повторите еще раз")
            continue
        value = int(value)
        if str(board[value - 1]) in "XO":
            print("эта клетка уже занята, повторите еще раз")
            continue
        board[value - 1] = n
        break


def check_win():
    for i in win_position:
        if (board[i[0] - 1]) == (board[i[1] - 1]) == (board[i[2] - 1]):
            return board[i[1] - 1]
    else:
        return False



def main():
    k = 0
    while True:
        draft_board()
        if k % 2 == 0:
            take_input("X")
        else:
            take_input("O")
        if k > 3:
            winer = check_win()
            if winer:
                draft_board()
                print(winer, "выиграл")
                break
        k += 1
        if k > 8:
            draft_board()
            print("Ничья")
            break

main()
