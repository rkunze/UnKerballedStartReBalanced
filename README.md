# UnKerballed Start ReBalanced

_UnKerballed Start ReBalanced_ rebalances the [UnKerballed Start] tech tree for a more realistic setup where

* The universe is around 1/4 real life scale (or about 2.5 to 3 times stock scale).
* Kerbals need life support.
* Parts can (and do) fail or wear out.
* Reaction wheels have realistic performance.
* Gathering scientifc data needs time.
* Engines have limited ignitions.
* Ullage motors may be necessary in order to (re-)start engines in free fall.
* Rocket launches and space missions are highly automated.

Another main design goal for _UnKerballed Start ReBalanced_ is to do this with a minimum number of installed part mods and minimal overap between different parts. A career game with _UnKerballed Start ReBalanced_ will work well with only [ReStock+] (and [ReStock], since [ReStock+] depends on it) installed, although it will not have any parts. Other mods are used to fill in the later parts of the tech tree which are not covered by parts in _ReStock_ and _ReStock+_ or to fill specific niches, but in general, _UnKerballed Start ReBalanced_ tries to avoid having multiple parts that fill the exact same niche in the game.

In particular, _UnKerballed Start ReBalanced_ does not (and probably will never) support [BDB], [Tantares], [KNES] and similar mods that provide a huge number of parts inspired by actual real life rocketry and space craft. While those mods are truly excellent, they do not fit the design goals for _UnKerballed Start ReBalanced_, and they are already well supported by existing tech trees like the [Gradual Progression Tree], the [Skyhawk Science System] or the orginal [UnKerballed Start].

_UnKerballed Start ReBalanced_ is developed and tested with these mods to provide the "mostly realistic" game setup described above:

* [JNSQ] to scale the planetary system to 1/4 real life size
* [Kerbalism] for life support, science gathering and part failures
* [Engine Ignitor Re-ignited] for limited engine ignitions and ullagge simulation
* [kOS] and [Kerbalism] for automation
* This small custom [Module Manager] patch to nerf reaction wheels to 1% of their stock performance  
  ``` { .cfg file=Extra/NerfReactionWheels.cfg.optional }
  // All reaction wheels without air intake have only 1% of their stock torque.
  // Parts with reaction wheels and air intake stay at stock torque because 
  // some helicopter rotor parts use the reaction wheel module to simulate cyclic 
  // rotor controls
  @PART[*]:HAS[@MODULE[ModuleReactionWheel],!RESOURCE[IntakeAir]]:FINAL {
    @MODULE[ModuleReactionWheel] {
      @PitchTorque *= 0.01
      @YawTorque *= 0.01
      @RollTorque *= 0.01
    }
  }
  ```
  The (dectivated) patch is included as [`Extra/NerfReactionWheels.cfg.optional`](Extra/NerfReactionWheels.cfg.optional)

Note that none of those mods are needed to play with _UnKerballed Start ReBalanced_ — it should work just as well without any of them or with different mods that create similar conditions.

## Dependencies and Supported Mods

### Dependencies

The only hard dependencies of _UnKerballed Start ReBalanced_ are
* [UnKerballed Start] because _UnKerballed Start ReBalanced_ is implemented as a bunch of MM patches on top of _UnKerballed Start_.
* [Module Manager] because you can't apply those patches without it.
* [Community Tech Tree] because _UnKerballed Start_ depends on it.
* [ReStock+] because it provides a number of crucial parts for sounding rockets and early orbital rockets. It might be possible to make _UnKerballed Start ReBalanced_ work with the _Making History_ DLC instead of _ReStock+_ since there is quite a bit of overlap between both, but currently there are no plans to do so.
* [ReStock] because _ReStock+_ depends on it.

### Recommended Mods

These mods are recommended for playing with _UnKerballed Start ReBalanced_

* [JNSQ] or another system rescale mod to scale the planetary system to about 1/4 real life scale. _UnKerballed Start ReBalanced_ should work with other scales, but those have not been extensively tested (and bigger scales would probably need at least some changes to fuel tanks and engines to adapt their performance)
* [Kerbalism] for its unique scientific system. _UnKerballed Start ReBalanced_ should work without it, but has been developed with _Kerbalism_ in mind and not extensively tested without it
* [Hide Empty Tech Tree Nodes], especially if not all of the recommended part modes that fill out the later tree are installed

### Supported Mods

These mods are entirely optional for playing with _UnKerballed Start ReBalanced_, but integrated into and tested to work well with _UnKerballed Start ReBalanced_.

* [Principia] — Adds more realism by replacing the patched conics orbital mechanics simulation with n-body orbital mechanics, but does not affect the tech tree 
* [Engine Ignitor Re-ignited] — provides a need for those ullage motors and launch clamps. 
* [kOS] — provides fully programmable simulated computers to automate your space craft

### Other mods

Tech tree mods other than [UnKerballed Start] and [Community Tech Tree] are incompatible with _UnKerballed Start ReBalanced_.

Visual mods and QoL mods should be compatible with _UnKerballed Start ReBalanced_.

Planetary Rescale mods should work out of the box for scales up to 3 times stock scale. For larger scales, additional mods like [SMURFF] or [JNSQ Part Rebalancer] are needed to adapt the stock tanks and engines for that scale.

Other part mods as those mentioned in [Supported Mods](#supported-mods) will technically work if they are compatible with [UnKerballed Start] and/or [Community Tech Tree], but probably not fit into the progression and game balance set up by _UnKerballed Start ReBalanced_. Big part mods that recreate historical space craft (like [BDB], [Tantares], [KNES], ...) will most likely work less well than small part mods that just fill a specific niche.

## Installation

### CKAN

Will be available on CKAN after release.

### Manually using Git

Clone the GitHub repository in your `GameData` directory:

~~~ sh
cd $KSP_DIR/GameData
git clone https://github.com/rkunze/UnKerballedStartReBalanced.git
~~~

This requires that you have [Git](https://git-scm.com/) installed on your computer, but allows to update _UnKerballed Start ReBalanced_ later on with a simple `git pull`.

This is the recommended way to install a development version which is not yet released on CKAN.

### Manually without a Git client (not recommended)

As an alternative if you do not have Git, [download the current development status](https://github.com/rkunze/UnKerballedStartReBalanced/archive/refs/heads/main.zip) (or any version you want), unpack the zip file within your `GameData` directory, and rename `GameData/UnKerballedStartReBalanced-*` to `GameData/UnKerballedStartReBalanced`. For updates, you need to delete the `GameData/UnKerballedStartReBalanced` directory and reinstall from scratch.


[UnKerballed Start]: https://forum.kerbalspaceprogram.com/topic/196589-*
[Community Tech Tree]: https://forum.kerbalspaceprogram.com/topic/90530-*
[Gradual Progression Tree]: https://forum.kerbalspaceprogram.com/topic/226275-*
[Skyhawk Science System]: https://forum.kerbalspaceprogram.com/topic/206109-*
[ReStock]: https://forum.kerbalspaceprogram.com/topic/182679-*
[ReStock+]: https://forum.kerbalspaceprogram.com/topic/182679-*
[Engine Ignitor Re-ignited]: https://forum.kerbalspaceprogram.com/topic/168424-*
[Kerbalism]: https://forum.kerbalspaceprogram.com/topic/190382-*
[JNSQ]: https://forum.kerbalspaceprogram.com/topic/184880-*
[kOS]: https://forum.kerbalspaceprogram.com/topic/165628-*
[Module Manager]: https://forum.kerbalspaceprogram.com/topic/50533-*
[Modular Launchpads]: https://forum.kerbalspaceprogram.com/topic/173008-*
[SMURFF]: https://forum.kerbalspaceprogram.com/topic/117992-*
[JNSQ Part Rebalancer]: https://forum.kerbalspaceprogram.com/topic/184880-*
[Real Chute]: https://forum.kerbalspaceprogram.com/topic/52931-*
[BDB]: https://forum.kerbalspaceprogram.com/topic/122020-*
[Tantares]: http://forum.kerbalspaceprogram.com/topic/73686-*
[KNES]: http://forum.kerbalspaceprogram.com/topic/164035-*
[Principia]: https://github.com/mockingbirdnest/Principia
[Hide Empty Tech Tree Nodes]: https://forum.kerbalspaceprogram.com/topic/118305-*