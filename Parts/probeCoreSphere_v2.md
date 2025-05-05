# _**Probodobodyne Stayputnik**_ – `probeCoreSphere_v2`

The _**Probodobodyne Stayputnik**_ is revamped here to get it a bit closer to its real world counterpart [Sputnik-1], and to make it actually usable for both satellite and longer suborbital missions
* It has a battery capacity of a whopping 800 EC, and the `ModuleCommand` function uses only 0.0018 EC per second. This gives it a maximal operation time of a bit more than 20 days at stock scale with 6 hour days, and still about 10 days at JNSQ scale with 12 hour days (shorter if experiments are run which also need EC).

Based on mass and volume of the _**Z-100**_ battery, that storage capacity fits into the volume and mass of the original _**Stayputnik**_ with enough room to spare for housing and electronics, so mass can stay the same.

To balance the enormous EC storage and to prevent misuse of the _**Stayputnik**_ as a cheap battery, some other stats are adjusted:
* Cost is adjusted upwards to be more expensive than eight _**Z-100**_ batteries.
* `fuelCrossFeed` is set to `false` which prevents EC to be transmitted to node attached parts.
* `hasHibernation` is set to `false`

``` { .cfg #probeCoreSphere_v2 file=./Parts/probeCoreSphere_v2.cfg }
@PART[probeCoreSphere_v2]:NEEDS[ReStock,UnKerballedStart]:AFTER[ReStockPlus] {
    @description = #uksrb-probeCoreSphere_v2-description
    @cost = 900
    %fuelCrossFeed = false

    @RESOURCE[ElectricCharge] {
        @amount = 800
        @maxAmount = 800
    }
    @MODULE[ModuleCommand] {
        @RESOURCE[ElectricCharge] {
            @rate = 0.0018
        }
        %hasHibernation = false
    }

}
```
The _**Stayputnik**_ also gets a new description which emphasises its capabilities and does not mention crew safety (because there _are_ now crewed spaceraft yet).

``` { .cfg #localization-en-us }
#uksrb-probeCoreSphere_v2-description = The Stayputnik is the answer to the question of "how do we do science in space?". A lightweight sphere equipped with remote receivers and relay control input from the ground to the craft, its built-in batteries provide enough electricity to run experiments for several days before power runs out. Some assembly required. Antennas not included.
```


[Sputnik-1]: https://en.wikipedia.org/wiki/Sputnik_1
