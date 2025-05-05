# _**TB-0625 Structural Tube**_ – `uksrb-structural-tube-0625`  

A structural tube in 0.625m, downscaled from the 1.25m version provided by _ReStock+_.

Cost and mass of the part are scaled down to 1/4 because the structural tube is mostly empty space, meaning its cost and mass scale with the surface area of the walls and not the volume of the tube. Part volume, of course, is scaled by 1/8.

Entry cost is arbitrarily set to half of the entry cost for the next bigger structural type.

``` { .cfg #structural-tube-0625 file=./Parts/uksrb-structural-tube-0625.cfg }
+PART[restock-structural-tube-125-1]:NEEDS[ReStock,UnKerballedStart]:AFTER[ReStockPlus] {
    @name = uksrb-structural-tube-0625
    @title = #uksrb-structural-tube-0625-title

    @rescaleFactor = 0.5

    %scale = 0.625
    @cost /= 4
    @mass /= 4
    @entryCost /= 2
    @MODULE[ModuleCargoPart] {
        @packedVolume /= 8
    }

    @bulkheadProfiles = size0
    @node_stack_top1 = 0,0,0,0,-1,0,0
    @node_stack_bottom1 = 0,-0.1,0,0,1,0,0
    @node_stack_top2 = 0,0,0,0,1,0,0
    @node_stack_bottom2 = 0,-0.1,0,0,-1,0,0

    -MHReplacement = deleted

    @MODULE[ModulePartVariants] {
        @VARIANT[Short] {
            @cost /= 4
            @mass /= 4
            @NODES {
                node_stack_bottom2 = 0.0, -0.3125, 0.0, 0.0, -1.0, 0.0, 0
                node_stack_bottom1 = 0.0, -0.3125, 0.0, 0.0, 1.0, 0.0, 0
            }
        }
        @VARIANT[Medium-Short] {
            @cost /= 4
            @mass /= 4
            @NODES {
                node_stack_bottom2 = 0.0, -0.625, 0.0, 0.0, -1.0, 0.0, 0
                node_stack_bottom1 = 0.0, -0.625, 0.0, 0.0, 1.0, 0.0, 0
            }
        }
        @VARIANT[Medium] {
            @cost /= 4
            @mass /= 4
            @NODES {
                node_stack_bottom2 = 0.0, -0.9375, 0.0, 0.0, -1.0, 0.0, 0
                node_stack_bottom1 = 0.0, -0.9375, 0.0, 0.0, 1.0, 0.0, 0
            }
        }
        @VARIANT[Medium-Long] {
            @cost /= 4
            @mass /= 4
            @NODES {
                node_stack_bottom2 = 0.0, -1.25, 0.0, 0.0, -1.0, 0.0, 0
                node_stack_bottom1 = 0.0, -1.25, 0.0, 0.0, 1.0, 0.0, 0
            }
        }
        @VARIANT[Long] {
            @cost /= 4
            @mass /= 4
            @NODES {
                node_stack_bottom2 = 0.0, -1.875, 0.0, 0.0, -1.0, 0.0, 0
                node_stack_bottom1 = 0.0, -1.875, 0.0, 0.0, 1.0, 0.0, 0
            }
        }
    }

}
```

Localization texts for the 0.625m structural tube:

``` { .cfg #localization-en-us }
#uksrb-structural-tube-0625-title = TB-0625 Structural Tube
```
