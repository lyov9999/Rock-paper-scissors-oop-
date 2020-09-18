from random import randint

class Game:
    l = None

    def choose(self):
        your_choose =  None
        while not (type(your_choose) == int):
            try:
                your_choose=int(input('\n Input value '))
                if not (1 <= your_choose <= 3):
                    print('Input valid value !')
                    your_choose = None
            except:
                print('Input integer !')
        return your_choose

    def GetFinish(self, fin):
        while not (type(fin) == int):
            try:
                fin=int(input('Input finish score from the big 0 '))
                if fin < 1:
                    print('%s < 1' %fin)
                    fin = None
            except:
                print('Input integer !')
        return fin

    def compare(self, you, comp):
        if comp == 1:
            if you == 2:
                return 1
            elif you == 3:
                return 2
            else:
                return 3
        elif comp == 2:
            if you == 3:
                return 1
            elif you == 1:
                return 2
            else:
                return 3
        else:
            if you == 3:
                return 1
            elif you == 2:
                return 2
            else:
                return 3



game = Game()
game.l = {1:'rock', 2:'paper', 3:'scissors'}

you = comp = 0
finish = game.GetFinish(None)
while not (you == finish or comp == finish):
    comp_choose =  randint(1, 3)
    for k,v in game.l.items():
        print('  ', k,':',v  , sep=' ', end='', flush=True)

    your_choose = game.choose()

    your_compare = game.compare(your_choose, comp_choose)
    if your_compare == 1:
        you += 1
        print('\n{0} beats {1}\n'.format(game.l[your_choose], game.l[comp_choose]))
    elif your_compare == 2:
        comp +=1
        print('\n{0} beats {1}\n'.format(game.l[comp_choose], game.l[your_choose]))
    else:
        print('\nYour choose and Comp choose is %s\n' %game.l[your_choose])


    print('You: {0} || Comp: {1} \n'.format(you,comp))
