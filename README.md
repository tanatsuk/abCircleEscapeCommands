# AB Circle Escape Commands

Escape command `FF 00 41 01 00` GET POLLING CARD TYPE will likely return a `DF`, that is:

```
1101 1111
      ^^^
      |||
      ||+--polling on for iso14443 type a, e.g. credit cards
      |+---polling on for iso14443 type b, e.g. Japan driver's licnese
      +----polling on for felica, e.g. Japan rail pass
```

A user places on the card reader her/his wallet (which contains many cards). You want to home in on the felica and ignore the rest.

Escape command `FF 00 41 01 01 DC` SET POLLING CARD TYPE will clear/set the appropriate bits for you:

```
1101 1100
      ^^^
      |||
      ||+--polling off for iso14443 type a, e.g. credit cards
      |+---polling off for iso14443 type b, e.g. Japan driver's licnese
      +----polling on for felica, e.g. Japan rail pass
```

and your reader will be able to connect to the felica card and ignore the others.

The setting will persist after a power-cycle of the card reader. You can send escape command `FF 00 41 01 01 DF` SET POLLING CARD TYPE to get back to the old behavior
