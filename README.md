# GFMPW-1 rise & fall time measurements

Measured on a
[Caravel board](https://github.com/efabless/caravel_board/tree/main/hardware/development/caravel-dev-gf180-v6-M.2)
running the
[blink firmware](https://github.com/efabless/caravel_board/blob/main/firmware/gf180/blink/blink.c)
with this change by @smunaut to vary the drive strength:
```
#undef GPIO_MODE_MGMT_STD_OUTPUT
#define DRIVE 0
#define GPIO_MODE_MGMT_STD_OUTPUT (0x00b | (DRIVE << 8))
```
where `DRIVE` was set to `0`, `1`, `2`, `3`.

Power was supplied on the `vccd` pin from a generic benchtop PSU
and rise/fall times measured on `gpio[26]` using a Rigol DS1104Z scope.
Measurements were taken from the chip with id C7-058.

Average values from 10 measurements:

| DRIVE | 3.3V rise | 3.3V fall | 5V rise | 5V fall |
| ----: | --------: | --------: | ------: | ------: |
|     0 |    8.8 ns |    5.2 ns |  6.0 ns |  4.1 ns |
|     1 |    4.2 ns |    2.8 ns |  3.4 ns |  2.6 ns |
|     2 |    3.3 ns |    2.4 ns |  3.0 ns |  2.4 ns |
|     3 |    3.0 ns |    2.3 ns |  2.8 ns |  2.3 ns |
