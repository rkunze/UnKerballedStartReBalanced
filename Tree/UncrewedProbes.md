# Uncrewed Probes

## Design
### Base Setup: Parts from [ReStock] and [ReStock+]

The standard setup with [ReStock] and [ReStock+] installed provides a total of 16 uncrewed probe cores of four distinct types placed mainly along the _Uncrewed Probes_ tech tree branch

* **Satellite/Probe Cores**: Most of those are generic cores for building satellites or space probes

  * _**Probodobodyne QBE**_ `probeCoreCube` placed at `stability` in tier 3
  * _**Probodobodyne OKTO**_ `probeCoreOcto_v2` placed at `flightControl` in tier 4
  * _**Probodobodyne HECS**_ `probeCoreHex_v2` placed at `specializedControl` in tier 6
  * _**Probodobodyne OKTO2**_ `probeCoreOcto2_v2` placed at `unmannedTech` in tier 7
  * _**Probodobodyne HECS2**_ `HECS2_ProbeCore` placed at `largeUnmanned` in tier 9

  The rest are specialized parts modelled along real-world counterparts
  * _**Probodobodyne Stayputnik**_ `probeCoreSphere_v2` is a kerbalized replica of [Sputnik-1] placed at `start` in tier 1
  * _**MPO Probe**_ `MpoProbe` is the kerbalized version of the [Bepi-Colombo Mercury Planetary Orbiter] placed at `largeUnmanned` in tier 9
  * _**MTM Stage**_ `MtmStage` is the kerbalized version of the [Bepi-Colombo Mercury Transfer Module] placed at `largeUnmanned` in tier 9 

* **Rover Cores**: One core is a dedicated part for building rovers
  * _**Probodobodyne RoveMate**_ `roverBody_v2` placed at `flightControl` in tier 4

* **In-Stack Cores**: A series of advanced guidance cores for round stacks in different sizes
  * 0.625m: _**RC-XS1 Remote Guidance Unit**_ `restock-drone-core-0625-1`: placed at `specializedControl` in tier 6
  * 1.25m: _**RC-001S Remote Guidance Unit**_ `probeStackSmall` placed at `unmannedTech` in tier 7
  * 1.875m: _**RC-M001 Remote Guidance Unit**_ `restock-drone-core-1875-1` placed at `advUnmanned` in tier 8
  * 2.5m: _**RC-L01 Remote Guidance Unit**_ `probeStackLarge`: placed at `advUnmanned` in tier 8
  * 3.75m: _**RC-XL001 Remote Guidance Unit**_ `restock-drone-core-375-1` placed at `artificialIntelligence` in tier 10
* **Airplane/Spaceplane Cores**: The last type has two parts meant for uncrewed airplanes and spaceplanes 
  * 0.625m: _**CH-J3 Fly-By-Wire Avionics Hub**_ `avionicsNoseCone` at `specializedControl` in tier 6 on the _Uncrewed Probes_ tech tree branch.  Actually, this is only sort-of a core because it only provides SAS cpabilities but has no built in `ModuleCommand`.
  * MK2 form factor:  _**MK2 Drone Core**_ `mk2DroneCore` at `hypersonicFlight` in tier 8 on the _Aviation_ tech tree branch.

This original setup has a couple of problems:
* The `probeCoreSphere_v2` is the only probe core available in tiers 1 to 3, but is not well suited for atmospheric sounding rockets because of its spherical shape and a diameter larger than the 0.625m stack.
* The placement of the _**Remote Guidance Unit**_ series seems a bit haphazard. The smaller versions are a overpowered for their place in the tree, and placing the `restock-drone-core-375-1` all the way out in `artificialIntelligence` is just weird considering that 3.75m parts are common much earlier in the tree and the `restock-drone-core-375-1` is just (by that time) well established technology in a larger housing.
* The `avionicsNoseCone` as a dedicated SAS addon part at tier 6 is pretty much useless: At that point in the tree, every probe core or command pod that is not long obsolete already has some built-in SAS capabilities, and the (overpowered) 0.625m core from the _**Remote Guidance Unit**_ series even has the full set of SAS capabilites _and_ builtin reaction wheels.

**_UnKerballed Start ReBalanced_** tries to address those shortcomings by

* Recasting the [`avionicsNoseCone` as a full featured guidance core](../Parts/avionicsNoseCone) for atmospheric sounding rockets and drone aircraft. The part also gets renamed to "Aerodynamic Aircraft/Rocket Guidance Hub" just because of the obvious acronym, and made available in the [`start`] node.
* Remaking the [`probeCoreSphere_v2` as a dedicated, standalone satellite](../Parts/probeCoreSphere_v2.md) that is actually useful for early orbital missions. Available at [`stability`].
* Giving the in-stack _**Remote Guidance Unit**_ series a dedicated role as guidance systems for launch vehicles and (later in the game) big space stations. At the same time, they get a bit more variety and are placed earlier in the tree
  
  * [`restock-drone-core-0625-1`] is a guidance system for 0.625m launch vehicles and available at [`engineering101`] 
  * [`probeStackSmall`] fills the same role for 1.25m launch vehicles and is available at [`stability`].  
  * [`restock-drone-core-1875-1`] with integrated reaction wheels goes to [`flightControl`]  
  * The remaining two _**RGU**_ cores are meant to control large launch vehicles and space stations starting at late mid-game, keep their original stats, and are introduced in [`specializedControl`] and [`advUnmanned`].

  [`restock-drone-core-0625-1`]: ../Parts/restock-drone-core-0625-1.md
  [`probeStackSmall`]: ../Parts/probeStackSmall.md
  [`restock-drone-core-1875-1`]: ../Parts/restock-drone-core-1875-1.md
 
The rest of the basic probe cores are kept as is and distributed along the _Uncrewed Probes_ branch of the tech tree vas specified below.

## Tree Configuration for Tier 4 and Later

See [Early Game](./EarlyGame.cfg) for the configurations of tiers 1 through 3.

[`start`]: ./EarlyGame.md#start
[`engineering101`]: ./EarlyGame.md#engineering101
[`stability`]: ./EarlyGame.md#stability


### <a name="flightControl"></a> Tier 4: `flightControl`
[`flightControl`]: #flightControl
* [`restock-drone-core-1875-1`], `probeCoreCube` and `roverBody_v2`
  ``` { .cfg #UncrewedProbes file=./Tree/UncrewedProbes.cfg }
  @PART[restock-drone-core-1875-1,probeCoreCube,roverBody_v2]:NEEDS[ReStock,ReStockPlus]:AFTER[zzzUnKerballedStart] {
      @TechRequired = flightControl
  }
  ```

### <a name="advFlightControl"></a> Tier 5: `advFlightControl`
[`advFlightControl`]: #advFlightControl
* `probeCoreOcto_v2`
  ``` { .cfg #UncrewedProbes file=./Tree/UncrewedProbes.cfg }
  @PART[probeCoreOcto_v2]:NEEDS[ReStock,ReStockPlus]:AFTER[zzzUnKerballedStart] {
      @TechRequired = advFlightControl
  }
  ```

### <a name="specializedControl"></a> Tier 6: `specializedControl`
[`specializedControl`]: #specializedControl
* `probeStackLarge`, `mk2DroneCore` and `probeCoreHex_v2`
  ``` { .cfg #UncrewedProbes file=./Tree/UncrewedProbes.cfg }
  @PART[probeStackLarge,mk2DroneCore,probeCoreHex_v2]:NEEDS[ReStock,ReStockPlus]:AFTER[zzzUnKerballedStart] {
      @TechRequired = specializedControl
  }
  ```
  `mk2DroneCore` is placed here because this tier also has most of the MK2 form factor aircraft/spaceplane parts

### <a name="unmannedTech"></a> Tier 7: `unmannedTech`
[`unmannedTech`]: #unmannedTech
* `probeCoreOcto2_v2`
  ``` { .cfg #UncrewedProbes file=./Tree/UncrewedProbes.cfg }
  @PART[probeCoreOcto2_v2]:NEEDS[ReStock,ReStockPlus]:AFTER[zzzUnKerballedStart] {
      @TechRequired = unmannedTech
  }
  ```

### <a name="advUnmanned"></a> Tier 8: `advUnmanned`
[`advUnmanned`]: #advUnmanned
* `restock-drone-core-375-1`, `HECS2_ProbeCore`
  ``` { .cfg #UncrewedProbes file=./Tree/UncrewedProbes.cfg }
  @PART[restock-drone-core-375-1,HECS2_ProbeCore]:NEEDS[ReStock,ReStockPlus]:AFTER[zzzUnKerballedStart] {
      @TechRequired = advUnmanned
  }
  ```

### <a name="largeUnmanned"></a> Tier 9: `largeUnmanned`
[`largeUnmanned`]: #largeUnmanned
* `MpoProbe` and `MtmStage`. Unchanged from [UnKerballed Start].

### <a name="artificialIntelligence"></a> Tier 10: `artificialIntelligence`
[`artificialIntelligence`]: #artificialIntelligence

[Sputnik-1]: https://en.wikipedia.org/wiki/Sputnik_1
[Bepi-Colombo Mercury Planetary Orbiter]: https://en.wikipedia.org/wiki/BepiColombo#Mercury_Planetary_Orbiter
[Bepi-Colombo Mercury Transfer Module]: https://en.wikipedia.org/wiki/BepiColombo#Mercury_Transfer_Module
[UnKerballed Start]: https://forum.kerbalspaceprogram.com/topic/196589-*
[ReStock]: https://forum.kerbalspaceprogram.com/topic/182679-*
[ReStock+]: https://forum.kerbalspaceprogram.com/topic/182679-*


