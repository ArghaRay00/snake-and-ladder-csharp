# Snake and Ladder Game

A console-based Snake and Ladder game in C# with configurable boards. You define the snakes, ladders, and players via console input — the game handles turns, dice rolls, chaining (landing on a ladder that leads to a snake), and win detection.

Built this as a low-level design exercise — the kind of problem you'd get in a machine coding round.

## How it works

- 100-cell board, configurable snakes and ladders
- Players take turns rolling a dice (1-6)
- Land on a ladder start = climb to the end
- Land on a snake head = slide to the tail
- Chaining: if a ladder drops you on a snake (or vice versa), it keeps resolving until stable
- Must land exactly on 100 to win — overshooting stays in place
- Queue-based turns — winners exit, game continues for remaining players

## Design

| Class | Responsibility |
|-------|----------------|
| `Player` | Name + unique ID |
| `Snake` | Head and tail positions |
| `Ladder` | Start and end positions |
| `DiceService` | Static `roll()` returns random 1-6 |
| `SnakeAndLadderBoard` | Board size, snakes list, ladders list, player positions |
| `SnakeAndLadderService` | Game engine — turn management, position updates, win detection |
| `Program` | Console I/O — reads board config, starts game |

## Sample Board

![Board](https://github.com/ArghaRay00/SnakeAndLadderGame/blob/master/docs/Board.JPG)

## Input Format

```
9                    # number of snakes
62 5                 # snake: head at 62, tail at 5
33 6
49 9
88 16
41 20
56 53
98 64
93 73
95 75
8                    # number of ladders
2 37                 # ladder: start at 2, end at 37
27 46
10 32
51 68
61 79
65 84
71 91
81 100
2                    # number of players
Argha
Ritwick
```

## Running it

```bash
dotnet build
dotnet run
```

## Tech

C# console application, .NET Core 3.1

## License

MIT
