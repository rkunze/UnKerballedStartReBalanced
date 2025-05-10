# Chemical Rockets

## Design

The chemical rockets branch has all liquid and solid fuel rocket engines. It start directly off the `start` node and branches again at tier 5 into a _Heavy Rocketry_ branch for mostly lifter engines, and a _Propulsion Systems_ branch for smaller and mostly vacuum optimized engines.

Non-chemical rockets (nuclear and ion) have their own branches.

### Base Setup: Parts from [ReStock] and [ReStock+]

Setup is mostly left unchanged from [UnKerballed Start] with a few exceptions:
* The `sepMotor1` ("Sepratron")is available at [`generalRocketry`] to provide an ullage motor if [Engine Ignitor Re-ignited] or another ullage simulation is installed.
* The [`radialEngineMini_v2`] (_LV-R1 "Spider"_) is available at [`basicRocketry`] to provide control for liquid fueled rockets.
* The R-7/Soyuz inspired parts are all available at tier 4 (in [UnKerballed Start], the engines are in tier 5 and the conical booster tanks in tier 6)
* The [`radialLiquidEngine1-3`] (_Mk-55 "Thud"_) is pushed to at [`precisionPropulsion`] at tier 6 because it feels overpowered for tier 4 (and the real world inspiration was probably the [STS OMS](https://en.wikipedia.org/wiki/Orbital_Maneuvering_System) which would place it even later).
* The `Sìze3AdvancedEngine` (_KR-2L+ "Rhino"_) is moved from tier 11 to [`specializedRocketry9`] at tier 9 because tiers 10 and up are for future tech, and stock parts cover technologies up to real-world present at best.

### Mod Support: [Engine Ignitor Re-ignited]

The most important part of the support is already in the tree by default: Providing ullage motors early enough for the first engines with internal ignitors. The rest of the support consists in moving the engine upgrades from their original position in the engineering and electrics branches to the corresponding tiers in the propulsion branch.

## Tree Configuration for Tier 4 and Later

See [Early Game](./EarlyGame.cfg) for the configurations of tiers 1 through 3.

[`start`]: ./EarlyGame.md#start
[`basicRocketry`]: ./EarlyGame.md#basicRocketry
[`generalRocketry`]: ./EarlyGame.md#generalRocketry

### <a name="advRocketry"></a> Tier 4: `advRocketry`
[`advRocketry`]: #advRocketry
* `restock-engine-panda-1`/`LiquidEngineRV-1`, `restock-engine-ursa-1`/`LiquidEngineRK-7`
  ``` { .cfg #ChemicalRockets file=./Tree/ChemicalRockets.cfg }
  @PART[restock-engine-panda-1,LiquidEngineRV-1,restock-engine-ursa-1,LiquidEngineRK-7]:NEEDS[ReStock,ReStockPlus]:AFTER[zzzUnKerballedStart] {
      @TechRequired = advRocketry
  }
  ```

### <a name="precisionPropulsion"></a> Tier 6: `precisionPropulsion`
[`precisionPropulsion`]: #precisionPropulsion
* `radialLiquidEngine1-2`
  ``` { .cfg #ChemicalRockets file=./Tree/ChemicalRockets.cfg }
  @PART[radialLiquidEngine1-2]:NEEDS[ReStock,ReStockPlus]:AFTER[zzzUnKerballedStart] {
      @TechRequired = precisionPropulsion
  }
  ```


### <a name="specializedRocketry9"></a> Tier 9: `specializedRocketry9`
[`specializedRocketry9`]: #specializedRocketry9
* `Size3AdvancedEngine`
  ``` { .cfg #ChemicalRockets file=./Tree/ChemicalRockets.cfg }
  @PART[Size3AdvancedEngine]:NEEDS[ReStock,ReStockPlus]:AFTER[zzzUnKerballedStart] {
      @TechRequired = specializedRocketry9
  }
  ```

[ReStock]: https://forum.kerbalspaceprogram.com/topic/182679-*
[ReStock+]: https://forum.kerbalspaceprogram.com/topic/182679-*
[Engine Ignitor Re-ignited]: https://forum.kerbalspaceprogram.com/topic/168424-*
[UnKerballed Start]: https://forum.kerbalspaceprogram.com/topic/196589-*