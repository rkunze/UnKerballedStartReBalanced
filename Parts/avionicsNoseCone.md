# _**AARGH Aerodynamic Aircraft/Rocket Guidance Hub**_ – `avionicsNoseCone`

The _**Aerodynamic Aircraft/Rocket Guidance Hub**_ is an integrated guidance core and experiment platform built for early sounding rockets and uncrewed aircraft. Stats and cost reflect the position at the start of the tech tree.

Other than most other probe cores, it comes with a builtin antenna capable of transmitting science results. That antenna has a very reduced range, though – with the stock range formula, just about 50 km against the level 1 DSN.

``` { .cfg #avionicsNoseCone file=./Parts/avionicsNoseCone.cfg }
@PART[avionicsNoseCone]:NEEDS[ReStock,UnKerballedStart]:AFTER[ReStockPlus] {
    @title = #uksrb-avionicsNoseCone-title
    @description = #uksrb-avionicsNoseCone-description
    @manufacturer = Research & Development Department
    @cost = 400
    @entryCost = 2000
    @tags = #autoLOC_500360 //#autoLOC_500360 = command control (core kerbnet probe satellite space steer
    @category = Pods
    @subcategory = 0
    %vesselType = Probe

    !MODULE[ModuleSAS] {}
    MODULE {
        name = ModuleSAS
        SASServiceLevel = 0
    }

    MODULE {
        name = ModuleCommand
        minimumCrew = 0
        RESOURCE {
            name = ElectricCharge
            rate = 0.03
        }
        hasHibernation = False
    }

    MODULE {
        name = ModuleDataTransmitter
        antennaType = DIRECT
        packetInterval = 0.6
        packetSize = 2
        packetResourceCost = 12.0
        requiredResource = ElectricCharge
        antennaPower = 1.25
        antennaCombineable = False
    }

    RESOURCE {
        name = ElectricCharge
        amount = 75
        maxAmount = 75
    }
}
```
The title and description reflects the new capabilites and role of the part

``` { .cfg #localization-en-us }
#uksrb-avionicsNoseCone-title = AARGH Aerodynamic Aircraft/Rocket Guidance Hub
#uksrb-avionicsNoseCone-description = Developed inhouse at the Research & Development Department under the lead of Wernher von Kerman himself, the Aerodynamic Aircraft/Rocket Guidance Hub is the core (not to mention the pride and joy) of the budding space program. It provides radio control, scientific experiments and an integrated power source, and can be used to remotely pilot both rockets and aircraft. Including those that are deemed to dangerous to pilot by even the redoubtable Jebediah Kerman. It even includes an experimental "stability assist system" that can keep the vehicle automatically pointed in a given direction. (If said vehicle has suitable actuators).
```

## Mod Support

Some values need to be adjusted when certain mods are installed. 

### Custom Barn Kit
[Custom Barn Kit] allows to change the DSN range. Account for that by recalculating the correct `antennaPower` for a range of 50km against the level 1 DSN. Connection range is calculated as _√(a·d)_ where _a_ is the `antennaPower` setting and _d_ is the DSN range. Equating the range to 50 km and solving for _a_ gives the value for `antennaRange` as _(50000)²/d = 2500000000/d_.

``` { .cfg #avionicsNoseCone file=./Parts/avionicsNoseCone.cfg }
@PART[avionicsNoseCone]:NEEDS[ReStock,ReStockPlus,UnKerballedStart,CustomBarnKit]:LAST[zzzUnKerballedStart] {
    @MODULE[ModuleDataTransmitter] {
        @antennaPower = 2500000000
        @antennaPower /= #$@CUSTOMBARNKIT/TRACKING/DSNRange[0]$
    }
}
```

This patch is run here as `LAST[zzzUnKerballedStart]` in the hope that all other patches that modify the DSN range are already applied.

### JNSQ
[JNSQ] adjusts `antennaPower` upward by a factor of 4 for all antennas, and recommends a DSN multiplier of 4 as well. To counteract this, reduce the antenna power by a factor of 4 (to counteract the DSN modifier) and another factor of 4 to revert the JNSQ patch that increased `antennaPower`. Note that the last step must only be applied if [Custom Barn Kit] is not installed, because if it is installed, the patch in the section above already recalculated the correct `antennaPower` for a DSN modifier of 1. Also runs as `LAST[zzzUnKerballedStart]` to get the correct patch order when the [Custom Barn Kit] patch above is used.

``` { .cfg #avionicsNoseCone file=./Parts/avionicsNoseCone.cfg }
@PART[avionicsNoseCone]:NEEDS[ReStock,ReStockPlus,UnKerballedStart,JNSQ]:LAST[zzzUnKerballedStart] {
    @MODULE[ModuleDataTransmitter] {
        @antennaPower /= 4
        @antennaPower:NEEDS[!CustomBarnKit] /= 4
    }
}
```

### VAB Organizer

If [VAB Organizer] is installed, make sure that the part is sorted into the correct category. Runs as `LAST[zzzUnKerballedStart]` to be reasonably sure that it is applied after all other [VAB Organizer] support patches, but still gives the player a chance to override it with a custom `FINAL` patch.

``` { .cfg #avionicsNoseCone file=./Parts/avionicsNoseCone.cfg }
@PART[avionicsNoseCone]:NEEDS[ReStock,ReStockPlus,VABOrganizer]:LAST[zzzUnKerballedStart] {
  %VABORGANIZER
  {
    %organizerSubcategory = probes
  }
}
```

[VAB Organizer]: https://forum.kerbalspaceprogram.com/topic/225794-*
[JNSQ]: https://forum.kerbalspaceprogram.com/topic/184880-*
[Custom Barn Kit]: https://forum.kerbalspaceprogram.com/topic/109027-*