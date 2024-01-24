# Texas_holdem_python_engine
This is a Python library for playing Texas poker

# How to start
First is to install the library by running the following command in the terminal:
'''
pip install git+https://github.com/LarkMi/Texas_holdem_python_engine.git
'''
Then

'''
from texas_holdem import Game

games_info = {
    'names': ['player1', 'player2', 'player3', 'player4']
    'small_blind': 10,
    'big_blind': 20,
    'buy_in': 2000
    'chips': {
        'player1': 1000,
        'player2': 2000,
        'player3': 3000,
        'player4': 4000
    } # 'chips' is optional, if not provided, all players start with 'buy_in' chips
}

game = Game(games_info)
# you can use game.games_info to show the game information
# game.player_to_action 
# use game.round(name, action) to do action for player
# description of the cards:
# card : (size, decor)
# size in range(2,15), represent 2-A; decor in range(1,5)
# example:
while game.current_state != 'finished':
    player_name = game.player_to_action
    need_to_call = game.max_bet - game.games_info['bet_chip'][player_name]
    game.round(player_name, need_to_call)

# Restart game
game.restart()
'''