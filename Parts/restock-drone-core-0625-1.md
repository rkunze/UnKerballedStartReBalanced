# _**RC-XS1 Remote Guidance Unit**_ – `restock-drone-core-0625-1`

The `restock-drone-core-0625-1` is adapted to its new place early in the game and its role as guidance system for launch vehicles:
* `ModuleProbeControlPoint`, `ModuleReactionWheel` and `ModuleScienceContainer` are removed
* `ModuleSAS` remains but is stripped down to SAS level 0 (attitude hold only)
* Cost is reduced to 400
* Unlock cost is reduced to 2000

This gets the stats to about those of the `probeCoreSphere_v2` (_**Stayputnik**_), but with SAS capability (which justifies the higher cost of 400 versus 300 funds).

SAS capability is upgraded later in the tree, see [SAS-upgrades.md](./SAS-Upgrades.md)

``` { .cfg #restock-drone-core-0625-1 file=./Parts/restock-drone-core-0625-1.cfg }
@PART[restock-drone-core-0625-1]:NEEDS[ReStock,UnKerballedStart]:AFTER[ReStockPlus] {
    @description = #uksrb-restock-drone-core-0625-1-description
    @cost = 400
    @entryCost = 2000

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
#uksrb-restock-drone-core-0625-1-description = The STEADLER RGU core is one of the most complete command units available to date, featuring all the latest guidance systems. STEADLER claims this is the perfect guidance module for the most advanced rockets. (Some assembly required. Rocket sold separately).
```

