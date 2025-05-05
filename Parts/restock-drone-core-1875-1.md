# _**RC-M001 Remote Guidance Unit**_ – `restock-drone-core-1875-1`

[ReStock+]: https://forum.kerbalspaceprogram.com/topic/182679-*

The `restock-drone-core-1875-1` is adapted to fit its new place as an early-mid game launch vehicle and space station control core:
* `ModuleProbeControlPoint` and `ModuleScienceContainer` are removed
* `ModuleSAS` remains but is stripped down to SAS level 0
* `ModuleReactionWheel` is retained, making it the first inline core with integrated reaction wheels
* Cost is reduced to 1500
* Unlock cost is reduced to 5000

SAS capability is upgraded later in the tree, see [SAS-upgrades.md](./SAS-Upgrades.md)

``` { .cfg #restock-drone-core-1875-1 file=./Parts/restock-drone-core-1875-1.cfg }
@PART[restock-drone-core-1875-1]:NEEDS[ReStock,UnKerballedStart]:AFTER[ReStockPlus] {
    @description = #uksrb-restock-drone-core-1875-1-description
    @cost = 1500
    @entryCost = 5000

    !MODULE[ModuleProbeControlPoint] {}
    !MODULE[ModuleScienceContainer] {}

    @MODULE[ModuleSAS] {
        @SASServiceLevel = 0
    }
}
```

The description reflects the new capabilites and role of the part

``` { .cfg #localization-en-us }
#uksrb-restock-drone-core-1875-1-description = The most advanced remote guidance unit yet, for even larger rockets and with extra gyroscopes. In fact, the added gyroscopes on this guidance unit are so powerful that they ably act as actuators and actually affect attitude. Brought to you by STEADLER Engineering. Also suitable for attitude control on space stations. (Pending crew rating. Space Station not included).
```
