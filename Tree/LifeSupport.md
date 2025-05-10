# Life Support

## Design
### Base Setup: Parts from [ReStock] and [ReStock+]

## Tree Configuration for Tier 4 and Later

See [Early Game](./EarlyGame.cfg) for the configurations of tiers 1 through 3.

[`start`]: ./EarlyGame.md#start
[`engineering101`]: ./EarlyGame.md#engineering101
[`stability`]: ./EarlyGame.md#stability

### <a name="enhancedSurvivability"></a> Tier 4: `enhancedSurvivability`
[`enhancedSurvivability`]: #enhancedSurvivability
* `evaJetpack`
  ``` { .cfg #LifeSupport file=./Tree/LifeSupport.cfg }
  @PART[evaJetpack]:NEEDS[ReStock,ReStockPlus]:AFTER[zzzUnKerballedStart] {
      @TechRequired = enhancedSurvivability
  }
  ```
