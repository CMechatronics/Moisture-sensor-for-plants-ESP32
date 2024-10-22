This code converts the values provided by the transducer and sets an upper and lower limit, thus creating a moisture measurement scale expressed as a percentage.

You will need to find an average of the values received in the serial monitor when dry, and then do the same when completely wet.

The average values will be substituted in the following constants:

```cpp
const int DRY_MEDIA_VALUE = "your dry average value";
const int WET_MEDIA_VALUE = "your wet average value";
```

The average value will be more accurate the more instantaneous values you include in the average. (I included 100 values).
