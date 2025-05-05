# Early Game: From Start to Orbit

The first three tiers of the tech tree cover the technological progress from the game start with a single primitive sounding rocket up to the first satellites and the first attempts to safe return from orbit:

* [Tier 1](#tier-1) starts off the game with the very first atmospheric sounding rocket
* [Tier 2](#tier-2) introduces liquid fueled rockets, airplanes, and more scientific experiments, which makes it possible to reach space on suborbital flights and paves the way to gather enough science to unlock the next tier
* [Tier 3](#tier-3) has enough rocketry to get to orbit, and introduces the first parts needed to get back from there in one piece

[UnKerballed Start]: https://forum.kerbalspaceprogram.com/topic/196589-*
[ReStock]: https://forum.kerbalspaceprogram.com/topic/182679-*
[ReStock+]: https://forum.kerbalspaceprogram.com/topic/182679-*

## Tier 1
### <a name="#start"></a> _**Start**_ – `start`
[_**Start**_]: #start
[`start`]: #start

The [`start`] node has just enough parts to get a primitive sounding rocket off the ground, run a simple scientific experiment, and transmit the experiment results. Note that there are no parachutes (at least none that are usable for a probe), no standalone antennas, and no standalone batteries — the first probe _has_ to use the (limited) builtin resources from the [`avionicsNoseCone`](../Parts/avionicsNoseCone).

#### [ReStock] and [ReStock+] parts

* [`avionicsNoseCone`](../Parts/avionicsNoseCone) - see also [`UncrewedProbes.md`](./UncrewedProbes.md)
  ``` { .cfg #EarlyGame file=./Tree/EarlyGame.cfg }
  @PART[avionicsNoseCone]:NEEDS[ReStock,ReStockPlus]:AFTER[zzzUnKerballedStart] {
      @TechRequired = start
  }
  ```
* `Mite`\
   Unchanged from [UnKerballed Start].
* `basicFin` \
   Unchanged from [UnKerballed Start].
* `sensorThermometer`\
   Unchanged from [UnKerballed Start].
* `evaChute` \
   Unchanged from [UnKerballed Start]. Should probably go to [`survivability`], but can't have the pilots lift off with whatever gets built once [`aeronautics`] unlocks without a parachute...

Two other purely decorative parts are also left at the start node
* `flagPartSize0`: Stock Part. Unchanged from [UnKerballed Start].
* `flagPartFlat`: Stock Part. Unchanged from [UnKerballed Start].

All other [ReStock] and [ReStock+] parts that are originally in _**Start**_ are moved to different nodes.

### _**Structures - tiny**_ – `structures0`

A cheap (1 science) node directly off the [_**Start**_] node with 0.625m structural parts. Mostly unchanged from [UnKerballed Start], with the sole exception of a small structural tube that can serve as extra space to put batteries and scientific instruments on more advanced sounding rockets.

* [`uksrb-structural-tube-0625`](../Parts/structural-tube-0625.md)
  ``` { .cfg #EarlyGame file=./Tree/EarlyGame.cfg }
  @PART[uksrb-structural-tube-0625]:NEEDS[ReStock,ReStockPlus]:AFTER[zzzUnKerballedStart] {
      @TechRequired = structures0
  }
  ```

## Tier 2

### <a name="basicRocketry"></a>_**Basic Rocketry**_ – `basicRocketry`
[`basicRocketry`]: #basicRocketry

### <a name="fabrication"></a>_**Fabrication**_ – `fabrication`
[`fabrication`]: #fabrication

### <a name="structures1"></a>_**Structures - small**_ – `structures1`
[`structures1`]: #structures1

A 1 science side node of [`fabrication`], with 1.25m structural parts. Unchanged from [UnKerballed Start].

### <a name="aeronautics"></a>_**Aeronautics**_ – `aeronautics`
[`aeronautics`]: #aeronautics

### <a name="wings1"></a>_**Wings 1**_ – `wings1`
[`wings1`]: #wings1

A 1 science side node of [`aeronautics`] with simple wing parts. Unchanged from [UnKerballed Start].

### <a name="engineering101"></a>_**Engineering 101**_ – `engineering101`
[`engineering101`]: #engineering101

Miscellaneus stuff from the [Science], [Electrics], [UncrewedProbes] and [Exploration] branches: More experiments, external batteries, an antenna with more range than 50km (but a bit fragile in thick atmosphere), an in-stack probe core as alternative to the [`avionicsNoseCone`][`start`], and a ladder to get into and out of aircraft.

* `sensorBarometer`\
   Unchanged from [UnKerballed Start].
* `batteryPack`
  ``` { .cfg #EarlyGame file=./Tree/EarlyGame.cfg }
  @PART[batteryPack]:NEEDS[ReStock,ReStockPlus]:AFTER[zzzUnKerballedStart] {
      @TechRequired = engineering101
  }
  ```
* `longAntenna`
  ``` { .cfg #EarlyGame file=./Tree/EarlyGame.cfg }
  @PART[longAntenna]:NEEDS[ReStock,ReStockPlus]:AFTER[zzzUnKerballedStart] {
      @TechRequired = engineering101
  }
  ```
* [`restock-drone-core-0625-1`](../Parts/restock-drone-core-0625-1.md)
  ``` { .cfg #EarlyGame file=./Tree/EarlyGame.cfg }
  @PART[restock-drone-core-0625-1]:NEEDS[ReStock,ReStockPlus]:AFTER[zzzUnKerballedStart] {
      @TechRequired = engineering101
  }
  ``` 
* `ladder1`\
   Unchanged from [UnKerballed Start].

## Tier 3

### <a name="stability"></a>_**Stability**_ – `stability`
[`stability`]: #stability

* `probeCoreSphere_v2` and `probeStackSmall`
  ``` { .cfg #EarlyGame file=./Tree/EarlyGame.cfg }
  @PART[probeCoreSphere_v2,probeStackSmall]:NEEDS[ReStock,ReStockPlus]:AFTER[zzzUnKerballedStart] {
      @TechRequired = stability
  }
  ```

### <a name="survivability"></a>_**Survivability**_ – `survivability`
[`survivability`]: #survivability

### <a name="gadgets"></a>_**Gadgets**_ – `gadgets`
[`gadgets`]: #gadgets

* `SurfAntenna`
  ``` { .cfg #EarlyGame file=./Tree/EarlyGame.cfg }
  @PART[SurfAntenna]:NEEDS[ReStock,ReStockPlus]:AFTER[zzzUnKerballedStart] {
      @TechRequired = gadgets
  }
  ```
* `solarPanels5`
  ``` { .cfg #EarlyGame file=./Tree/EarlyGame.cfg }
  @PART[solarPanels5]:NEEDS[ReStock,ReStockPlus]:AFTER[zzzUnKerballedStart] {
      @TechRequired = gadgets
  }
  ```
