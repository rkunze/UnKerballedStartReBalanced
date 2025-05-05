# _**RC-001S Remote Guidance Unit**_ – `probeStackSmall`

The `probeStackSmall` is adapted to its new place early in the game and its role as guidance system for launch vehicles:
* `ModuleProbeControlPoint`, `ModuleReactionWheel` and `ModuleScienceContainer` are removed
* `ModuleSAS` remains but is stripped down to SAS level 0 (attitude hold only)
* Cost is reduced to 600
* Unlock cost is reduced to 3000

SAS capability is upgraded later in the tree, see [SAS-upgrades.md](./SAS-Upgrades.md)

``` { .cfg #probeStackSmall file=./Parts/probeStackSmall.cfg }
@PART[probeStackSmall]:NEEDS[ReStock,UnKerballedStart]:AFTER[ReStockPlus] {
    @description = #uksrb-probeStackSmall-description
    @cost = 600
    @entryCost = 3000

    !MODULE[ModuleProbeControlPoint] {}
    !MODULE[ModuleReactionWheel] {}
    !MODULE[ModuleScienceContainer] {}

    @MODULE[ModuleSAS] {
        @SASServiceLevel = 0
    }
}
```
The description reflects the new capabilites and role of the part

``` { .cfg #localization-en-us }
#uksrb-probeStackSmall-description = The renowned STEADLER remote guidance unit, now sized for the latest and greatest rockets.
```

