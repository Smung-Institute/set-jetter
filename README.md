SET Jetter
---
(pronounced "set getter")

[Scikit Image](https://scikit-image.org/docs/stable/user_guide/getting_started.html)

[Playing Card Detection Using OpenCV-Python on the Raspberry Pi 3 + PiCamera](https://youtu.be/m-QPjO-2IkA)

[The Daily SET](https://www.setgame.com/set/puzzle)

[The Shepp-Logan Phantom teaches SET](https://www.youtube.com/watch?v=azaArSs-i0c)

[Knuth's anti-SET finder](https://www-cs-faculty.stanford.edu/~knuth/programs/setset-all.w)(WEB)


## Scale
Each card is unique in a deck of 81. A pair of cards determines a unique SET. There is only one third card in a deck that can make a SET with any two. ~~There are `81*80 == 6480` possible SETs~~. This double-counts. Less. 3240? Not a lot is the point. A tabular solution is easy.

## Card encoding

Set includes 81 cards, each with four qualities, and one of three choices for each quality. These qualities and options are
- Color
    - red
    - green
    - violet
- Symbol
    - oval
    - diamond
    - squingle
- Symbol count
    - 1
    - 2
    - 3
- Texture / filling
    - empty
    - scored
    - full

### card id

There are a few different ways to encode a distinct card.

- Cards given an id 0 to 80
    - ex. card 0 has one red empty oval. Card 1 has one red scored oval... Card 80 has three full violet squingles.
    - any consistent rotation of qualities / values over the whole deck is valid (ex exchanging all diamonds with ovals in the deck changes nothing in terms of assigning sets)
- ordered list of values
    - ex. `['r', 'd', 3, 's']`, `[0, 1, 3, 1]`, `[0, 1, 2, 1]` could all be the three-red-scored-diamonds card.
- dummy variable version:

| card id | is_green | is_violet | is_diamond | is_squingle | has_2 | has_3 | is_scored | is_full |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 12 | 0 | 0 | 1 | 0 | 0 | 1 | 1 | 0 |