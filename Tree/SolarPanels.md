# Solar Panels

## Design
### Base Setup: Parts from [ReStock] and [ReStock+]

## Tree Configuration for Tier 4 and Later

See [Early Game](./EarlyGame.cfg) for the configurations of tiers 1 through 3.

[`start`]: ./EarlyGame.md#start
[`engineering101`]: ./EarlyGame.md#engineering101
[`stability`]: ./EarlyGame.md#stability

### <a name="gizmos"></a> Tier 4: `gizmos`
[`gizmos`]: #gizmos
* `LgRadialSolarPanel`
  ``` { .cfg #SolarPanels file=./Tree/SolarPanels.cfg }
  @PART[LgRadialSolarPanel]:NEEDS[ReStock,ReStockPlus]:AFTER[zzzUnKerballedStart] {
      @TechRequired = gizmos
  }
  ```
