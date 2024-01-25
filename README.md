# Texas_holdem_python_engine
This is a Python library for playing Texas poker

# How to start
First is to install the library by running the following command in the terminal:
```
pip install git+https://github.com/LarkMi/Texas_holdem_python_engine.git
```
Then

```
from texas_holdem import Game

games_info = {
    'names': ['player1', 'player2', 'player3', 'player4'],
    'small_blind': 10,
    'big_blind': 20,
    'buy_in': 2000,
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
```
# Explanation
<table>
  <tr>
    <td colspan="3">Game.games_info</td>
  </tr>
  <tr>
    <td>names</td>
    <td>参与游戏的玩家姓名</td>
    <td>list[str]</td>
  </tr>
  <tr>
    <td>small_blind</td>
    <td>小盲注</td>
    <td>int</td>
  </tr>
  <tr>
    <td>big_blind</td>
    <td>大盲注</td>
    <td>int</td>
  </tr>
  <tr>
    <td>buy_in</td>
    <td>买入筹码量</td>
    <td>int</td>
  </tr>
  <tr>
    <td>chips</td>
    <td>玩家现有的筹码量</td>
    <td>dict[str:int]</td>
  </tr>
  <tr>
    <td>bet_chip</td>
    <td>玩家已下注的筹码量</td>
    <td>dict[str:int]</td>
  </tr>
  <tr>
    <td>public_cards</td>
    <td>公告牌</td>
    <td>list[(size, decor)]</td>
  </tr>
  <tr>
    <td>hand_cards</td>
    <td>玩家的手牌</td>
    <td>dict[str:list[(size, decor)]]</td>
  </tr>
  <tr>
    <td>all_in_player</td>
    <td>已all in的玩家姓名</td>
    <td>list[str]</td>
  </tr>
</table>

<table>
  <tr>
    <td colspan="2">Game</td>
  </tr>
  <tr>
    <td>max_bet</td>
    <td>最大下注量</td>
  </tr>
  <tr>
    <td>pot</td>
    <td>底池筹码量</td>
  </tr>
  <tr>
    <td>current_state</td>
    <td>目前的游戏状态</td>
  </tr>
  <tr>
    <td>player_to_action</td>
    <td>需要进行行动的玩家姓名</td>
  </tr>
</table>