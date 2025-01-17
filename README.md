# Low Visibility
This is a mod for the [HBS BattleTech](http://battletechgame.com/) game that introduces a new layer of depth into the detection mechanics of the game. These changes are influenced by the double-blind rules from MaxTech, but have been heavily adapted to the video game mechanics.

This mod has been designed to work with [RogueTech](http://roguetech.org). In theory is should work without that mod, but your mileage may vary.

__WARNING: THIS MOD LIKELY BREAKS SKIRMISH MULTIPLAYER.__ It has not been tested, but all due to the way it's been implemented my guess is that it won't work. You have been warned!

CAE is highly recommended. Many effects assume they aren't active at the same time (stealth/ecm, vision modes, etc.) You can enforce yourself through convention, or through CAE.

This mod requires the following mods. Grab the latest version of each of them and unzip them under your `BattleTech\Mods` folder:
* [IRBTModUtils](https://github.com/battletechmodders/IRBTModUtils/) - provides common logging and utility functions
* [CustomActivatableEquipment](https://github.com/battletechmodders/custombundle/) - replaces vanilla Auras with a far more performant one
* [CustomAmmoCategories](https://github.com/battletechmodders/custombundle/) - LowVis adds detail to the CAC terrain and unit popup dialog

This mod uses assets from [https://game-icons.net/], which are licensed through a CC BY 3.0 license. I've modified these icons by making them transparent, or changing the color of the icon, but otherwise they are unmodified. 

## Summary

This mod is comprehensive, but a short summary of changes in the mod include:

* Sensor blips can now be targeted and attacked, allowing long range builds to be more viable.
* ECM bubbles provide protection for allies and reduce enemy sensors.
* Enemy details are hidden and are only revealed to strong sensors and/or pilots with high Tactics.
* The environment can reduce visibility due to snow, rain, night, etc. This makes sensors critical to success on those maps.
* Stealth can hide enemy mechs (and your own!) allowing you to close range safely.
* Memetic armor reduces your ability to be targeted, but decreases if you move

## Configuration Reference

Configuration values in `mod.json` will be updated in the table below. If a section disagrees with this table, assume the table is correct

| Property | Description | Default |
| -- | -- | -- |
| Icon.ElectronicWarfare | The status bar icon used for the general EW information tooltip | `lv_eye-shield` |
| Icon.SensorsDisabled | The status bar icon used for the sensors disabled status | `lv_sight-disabled` |
| Icon.VisionAndSensors | The status bar icon used for the vision and sensors information tooltip | `lv_cyber-eye` |
| Icon.TargetSensorsMark | The unit icon used to indicate the player has sensor lock | `lv_radar-sweep` |
| Icon.TargetVisualsMark | The unit icon used to indicate the player has vision lock | `lv_brass-eye` |
| Icon.TargetTaggedMark | The unit icon used to indicate the unit is Tagged | `lv_target-laser` |
| Icon.TargetNarcedMark | The unit icon used to indicate the unit is Narced | `lv_radio-tower` |
| Icon.TargetStealthMark | The unit icon used to indicate the unit has Sensors Stealth| `lv_robber-mask` |
| Icon.TargetMimeticMark | The unit icon used to indicate the unit has Mimetic Stealth | `lv_static` |
| Icon.TargetECMShieldedMark | The unit icon used to indicate the unit has ECM Shielding | `lv_eye-shield` |
| Icon.TargetActiveProbePingedMark | The unit icon used to indicate the unit is pinged by an active probe | `lv_eye-target` |
| Icon.MarkColorPlayerPositive | The color used to indicate a unit icon is negative to the player | `[ 1.0, 0.0, 0.062, 1.0 ]` |
| Icon.MarkColorPlayerNegative | The color used to indicate a unit icon is negative to the player | `[ 0.0, 0.901, 0.098, 1.0 ]` |
| Toggles.LogEffectsOnMove | If true, effects on actors will be logged during position updates. | false |
| Toggles.ShowNightVision | If true, night-vision effects will be enabled during play. | true |
| Toggles.MimeticUsesGhost | If true, mimetic effects will use the GhostWeak VFX on the actor. | true |
| Sensors.MechRange | The default sensors range for a BattleMech | 360.0 |
| Sensors.TrooperRange | The default sensors range for a battle armor | 180.0 |
| Sensors.VehicleRange | The default sensors range for a vehicles | 270.0 |
| Sensors.TurretRange | The default sensors range for a turrets | 450.0 |
| Sensors.UnknownRange | The default sensors range when the unit type cannot be determined | 180.0 |
| Sensors.MinimumRange | The minimum range below which sensors cannot go. No roll or effect will reduce sensors below this limit. | 180.0 |
| Sensors.SensorsOfflineAtSpawn | If true, a unit's sensors will be reduced to `Sensors.MininumRange` for the turn it spawns | true |
| Sensors.MaxECMDetailsPenalty | The maximum penalty to sensor details that should be applied from jamming, shield, etc. | -9 |
| Sensors.MinSignature | The minimum signature a unit can have. Effects that reduce a unit's signature below this value will have no effect. | 0.05 |
| Vision.RangeBright | The default vision range for a unit when the map has the Bright mood. | 450.0 | 
| Vision.RangeDim | The default vision range for a unit when the map has the Dimmood. | 330.0 | 
| Vision.RangeDark | The default vision range for a unit when the map has the Dark mood. | 210.0 | 
| Vision.RangeMultiRainSnow | The multiplier to a unit's vision for the Ran or Snow weather condition. | 0.8 | 
| Vision.RangeMultiLightFog | The multiplier to a unit's vision for the Light Fog weather condition. | 0.66 | 
| Vision.RangeMultiHeavyFog | The multiplier to a unit's vision for the Heavy Fog weather condition. | 0.33 | 
| Vision.MinimumRange | The minimum range for vision that a unit can have. No weather or status effects can reduce a unit's vision below this level. | 90.0 | 
| Vision.ScanRange | The range at which a unit will achieve VisualID (i.e. visual scanning) on a target. This allows it to see armor and weapon types, but not details. | 210.0 | 
| FogOfWar.RedrawFogOfWarOnActivation | If true, the Fog Of War will be completely redrawn on each unit's activation. This will hide previously seen areas of the map, and only reveal the section of the map the current unit can observe. | false |
| FogOfWar.ShowTerrainThroughFogOfWar | If true, terrain in areas of the map that are still covered in the Fog of War will be hidden by a black mask. | true |
| Weather.LightFogDensity | The density of the fog effect for the Light Fog weather. | 3000 | 
| Weather.HeavyFogDensity | The density of the fog effect for the Heavy Fog weather. | 10000 |
| Attack.NoVisualPenalty | | 5 |
| Attack.NoSensorsPenalty | | 5 |
| Attack.FiringBlindPenalty | | 13 |
| Attack.ShieldedMulti | | 1.0 |
| Attack.JammedMulti | | 1.0 |
| Probability.Sigma | | 4 |
| Probability.Mu | | -1 |

## Target States

Every model in the game is in one of the three states. A target is either:

* **Visible** - your team can directly observing the target.
* **Detected** - your team tracks the target using sensors.
* **Unknown** - your team does not know the position of the target at all.

All allied units contribute towards determining if a model is visible or detected. If one unit can see a target, it passes that information to all other units on that team. However, each unit **individually** calculates whether it has a *Line of Sight* to the target, and what level of *Identification* it has for the target.

A unit has a *line of sight* to a target if it can directly observe the target. Line of sight can be obstructed by terrain such as hills, or reduced by weather conditions such as rain or fog. A line of sight can be *obstructed*, which means it partially passes through a terrain feature.

Even if a target is visible or detected, you may know its location but all other details can be hidden. **Identification** of the target's details comes from either visual inspection or sensor analysis:

* **Visual ID** - if you are close enough, your pilots can determine some basic information such as the chassis type, rough armor/structure values, and type of weapon. You have to be within 150 meters for visual identification.
* **Sensor ID** - with a good electronic warfare check your pilots can determine all of a target's details, including current armor values, weapon names, and component locations.

### Pilot Skill

Even the most advanced equipment depends upon the pilot... `TODO: CONTINUE ME`

### Equipment
	
This mod adds several types of equipment that generate electronic warfare effects. A short summary of their effects are:

* __ECM__ components generate a scrambling bubble that protects the carrier and friendly units within its area. This makes provides an attack penalty to attacks against friendly units, increases the difficulty of sensor identification against friendly units, and applies a penalty to sensor identification for any enemy unit within the area of effect.
* __Stealth__ components makes the equipped unit harder to detect by absorbing sensor emissions. They make the carrier harder to detect, increase the difficulty of sensor identification, and applies an attack penalty to any attacker.
* __Mimetic__ components make the unit harder to visually identify through a chameleonic effect. The carrier will be less visible and attacks will suffer a penalty. These effects are lost if the carrier moves during their turn.
* __Probe__ components are advanced sensors that make it easier to detect enemy units. They provide a bonus to sensor identification and reduce ECM, Stealth, and Mimetic effects on targets.
* __Narc__ weapons fire a transmitter the broadcasts data about the target across the entire map. This effect ignores Stealth and Mimetic effects on the target.
* __TAG__ weapons fire a specialized beam that locates and identifies a target. This effect is lost when the target moves. This effect ignores ECM or Stealth on the target.

## Details

This section describes the various mechanics that used throughout *LowVisibility*. Players may find this information overwhelming, as its written as a reference for mod authors.

While not necessary, it's suggested that you are familiar with the information in the [Low Visibility Design Doc](DesignDoc.md).

Any variable name in `code syntax` is a configuration value. It can be changed by modifying the named value in **LowVisibility/mod.json**.

### Electronic Warfare Checks
At the start of each round, every unit makes an **electronic warfare check** (EWC for short). A good check result represents the pilot making the best use of their equipment, while a poor one reflects them being preoccupied with other things.

Each check is a random value between -14 to +14, assigned from a normal distribution (aka a bell curve). The distribution uses mu=-2 and a sigma=4 value, resulting in a wide curve that's centered at the -2 result.

![Sensor Check Distribution](check_distribution.png "Sensor Check Distribution")

Each check is further modified by the source unit's tactics skill, as per the table below. (Skills 11-13 are for [RogueTech](http://roguetech.org) elite units).

| Skill |  1  |  2  |  3  |  4  |  5  |  6  |  7  |  8  |  9  |  10  | 11 | 12 | 13 |
| -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- |
| Modifier | +0 | +1 | +1 | +2 | +2 | +3 | +3 | +4 | +4 | +5 | +6 | +7 | +8 |
| w/ Lvl 5 Ability | +0 | +1 | +1 | +2 | +3 | +4 | +4 | +5 | +5 | +6 | +7 | +8 | +9 |
| w/ Lvl 8 Ability | +0 | +1 | +1 | +2 | +4 | +5 | +5 | +6 | +6 | +7 | +8 | +9 | +10 |

The current check result is displayed in a tooltip in the status bar of each player mech. The check result contributes to various calculations in the mod, including:

* As a bonus to visual identification
* As a bonus to sensor identification

### Spotting and Sensors

Every unit in the game has four related values that control whether it can be seen and targeted:

* **Spotting Range** determines how far away the source can visually locate a target. You can only draw a *line of sight* to a target at or within than your spotting range in meters.
* **Visibility** is a multiplier from the target that modifies the source's *spotting range*.
* **Sensor Range** determines how far away the unit can locate targets using sensors. You can only have sensor lock on a target at or within your sensor range in meters.
* **Signature** is a multiplier from the target that modifies the source's *sensor range*.

For both cases the math is straightforward. If a source has a 500 meter range, and the target has visibility/signature of 0.5, the target can be detected at 250 meters or closer. If the target's visibility/signature is 1.5, it can be detected at 750 meters or closer. 

Terrain design masks can modify visibility and signature values. Forests apply a 0.8 modifier to signature, while water applies a 1.2.

### Spotting

In *LowVisibility* unit's *base spotting range* is shorter than vanilla , as sensor locks allow targets to be identified and attacked. It can also be influenced by weather effects (see below). No matter the circumstances, a unit's spotting range cannot drop below `VisionRangeMinimum`. This value is expressed as 30 meter hexes, and defaults to 2 hexes (60 meters).

A MechWarrior can make some guesses about the target when they are very close. Units at `VisualIDRange` or will identify basic details about the target even if they have no sensor lock. Details will be limited to approximate armor and structure amounts, general weapon types, and the like. The default value is 5 hexes (180 meters).

TODO: Add EW check to effect to allow stronger pilots to know more

#### Environmental Effects

Each map contains one or more _mood_ tags, some of which apply a limit to all units spotting distance. Conceptually tags related to the ambient light level set the base vision range, while tags related to obscurement provide a multiplier that reduces this base range.

Any modifiers to a units _SpottingVisibilityMultiplier_ or _SpottingVisibilityAbsolute_ statistic increase the calculated base range.

Base Vision Range | Light |  Tags
-- | -- | --
15 hexes (450m) | bright | mood_timeMorning, mood_timeNoon, mood_timeAfternoon, mood_timeDay
11 hexes (330m) | dim | mood_timeSunrise, mood_timeSunset, mood_timeTwilight
7 hexes (210m) | dark | mood_timeNight

Vision Multiplier | Tags
-- | --
x0.7 | mood_weatherRain, mood_weatherSnow
x0.5 | mood_fogLight
x0.3 | mood_fogHeavy

> A map with _dim light_ and _rain_ has a vision range of `11 hexes * 30.0m * 0.7 = 231m`.

#### Sensor Range

The first check (the __range check__) is used to determine the unit's sensor range this turn. Each unit has a base sensor range determined by its type, as given in the table below. This range is increased by _SensorDistanceMultiplier_ and _SensorDistanceAbsolute_ values normally, allowing variation in unit sensor ranges.

| Type | Base Sensor Range |
| -- | -- |
| Mech | 12 hexes * 30m = __360m__ |
| Vehicle | 9 hexes * 30m = __270m__ |
| Turret | 15 hexes * 30m = __450m__ |
| Others | 6 hexes * 30m = __180m__ |

The range check result is divided by ten, then used as a multiplier against the unit's sensor range. A range check result of +3 yields a sensor range multiplier of (1 + 3/10) = 1.3x. A negative range check of -2 would result in a multiplier of (1.0 - 2/10) = 0.8x.

No matter the circumstances, sensors range cannot drop below a number of hexes equal to _SensorRangeMinimum_. This value defaults to 6 hexes (240 meters).

#### Target Details

The ***electronic warfare check*** also determines how many details about the target a source unit has access to this round. Enemy ECM, environmental effects, and other conditions will make this detailed information level fluctuate from round to round. Because every pilot and mech is different, the currently displayed details will cycle as you go through the round. A scout unit may have many details about the target available, while an assault unit may have very few. The range of check results is given below:

| Info Check | Detail Level | Details shown |
| --| -- | -- |
| < 0 | No Info | Failed sensor check, no information shown |
| 0 | Location | Target location (3d arrow), but unknown name |
| 1 | Type | As above, but type defined (mech/vehicle/turret) |
| 2 | Silhouette | As above, with Chassis as name (Atlas, Catapult) |
| 3 | Vector | As above, adding Evasion Pips |
| 4 or 5 | Surface Scan | As above, adding Armor & Structure percentages, paperdoll |
| 6 or 7 | Surface Analysis   | As above, adding Weapon Types (as colored ???) |
| 8 | Weapon Analysis | As above, with Weapon Names defined. Name is Chassis + Model (Atlas AS7-D, CPLT-C1) |
| 9 | Structure Analysis | As above, plus current heat & stability, summary info (tonnage, jump jets, etc). Armor & structure includes current and max values. Name is Chassis + Variant name (Atlas ASS-HAT Foo, Catapult CPLT-C1 Bar) |
| 10 | Deep Scan | As above plus component location, buffs and debuffs |
| 11 | Dental Records | As above plus pilot name, info |

### First Turn Protection

On the very first turn of every combat, every unit (friendly, neutral, or foe) always fail their __range check__. This ensures players can move away from their deployment zone before the AI has a chance to attack them. This behavior can be disabled by setting `FirstTurnForceFailedChecks` to __false__ in `mod.json`.


# Component and Status Effects

_LowVisibility_ is a toolkit designed to allow mod authors a great deal of flexibility. This flexibility comes at a cost, as each author has to understand how the various components work together. The mod is built from many differnet __effects__ which can be applied to components or as statuses to fit the mod needs. 

## Advanced Sensors

The BattleTech universe includes a complex array of sensors that improve a unit's ability to find enemies in specific situations. In _LowVisibility_ all of these advanced sensor types provide a bonus to the target details check. 

### Advanced Sensor Components

To create an Advanced Sensors  component, define the following effects on a componentDef. 

```json
          {
            "durationData" : {
                "duration": -1,
                "stackLimit": 1
            },
            "targetingData" : {
                "effectTriggerType" : "Passive",
                "specialRules" : "NotSet",
                "effectTargetType" : "Creator",
                "range" : 0.0,
                "forcePathRebuild" : false,
                "forceVisRebuild" : true,
                "showInTargetPreview" : true,
                "showInStatusPanel" : true
            },
            "effectType" : "StatisticEffect",
            "Description" :
            {
                "Id" : "LV_Advanced_Sensors",
                "Name" : "Advanced Sensors",
                "Details" : "Provides detailed information on enemy units",
                "Icon" : "uixSvgIcon_status_ECM-ghost"
            },
            "statisticData" : 
            {
                "statName" : "LV_ADVANCED_SENSORS",
                "operation": "Int_Add",
                "modValue": "2",
                "modType": "System.Int32"
            },
            "nature" : "Buff"
        },

```
## Active Probes

Active Probes are designed to counter-act ECM, Stealth, and other forms of obfuscation. _LowVisibility_ provides two active probe effects that reduce these values one for one. The first is a passive effect that always applies to the carrier unit. The second is a intended to be used for transient effects that originate from a 'ping', as per the HBS Active Probe system. 

The transient effect is stronger as it applies equally to all friendly units, while the passive effect only applies to the source unit.

### Active Probe Passive Effect

To create an Active Probe component that will always provide its effects passively to the source unit, define the following effects on a componentDef. This example will reduce any ECM, Stealth, or Mimetic effect by 3 points. 

```json
                  {
            "durationData" : {
                "duration": -1,
                "stackLimit": 1
            },
            "targetingData" : {
                "effectTriggerType" : "Passive",
                "specialRules" : "NotSet",
                "effectTargetType" : "Creator",
                "range" : 0.0,
                "forcePathRebuild" : false,
                "forceVisRebuild" : true,
                "showInTargetPreview" : true,
                "showInStatusPanel" : true
            },
            "effectType" : "StatisticEffect",
            "Description" :
            {
                "Id" : "LV_Probe_Carrier",
                "Name" : "Active Probe (Passive)",
                "Details" : "Reduces effectiveness of stealthed and ECM shielded units",
                "Icon" : "uixSvgIcon_status_ECM-ghost"
            },
            "statisticData" : 
            {
				"statName" : "LV_PROBE_CARRIER",
				"operation": "Int_Add",
				"modValue": "3",
				"modType": "System.Int32"
            },
            "nature" : "Buff"
        },
```

### Active Probe Transient Effect

To create an Active Probe effect that results from a ping, apply the following status effect. It will reduce any Stealth, ECM, or Mimetic effects by 6.

```json
      "effectType": "StatisticEffect",
      "Description": {
        "Id" : "ActiveProbe_Ping",
        "Name" : "ACTIVE PROBE PING",
        "Details": "AP Ping reduces Stealth, ECM, and Mimetic effects by 6",
        "Icon": "uixSvgIcon_status_sensorsImpaired"
      },
      "nature": "Debuff",
      "statisticData": {
        "statName": "LV_PROBE_PING",
        "operation": "Int_Add",
        "modValue": "6",
        "modType": "System.Int32"
      }
```

## ECM

ECM components generate an bubble of interference around the carrier unit. Friendly units within the bubble receives an **ECM Shield** effect. Enemy units within the bubble receive an **ECM Jamming** effect.

* For each point of **ECM Shield**, attackers gain a +1 attack penalty and -1 sensors identification check. The target gains a 0.1 *decrease* to their signature, making it harder for them to be located.
* For each point of **ECM Jamming** on a target, the target suffers a -1 penalty to any sensors identification check they make.

Both **ECM Jamming** and **ECM Shield** modifiers apply when a jammed source attempts to locate a shielded target. If there are multiple ECM sources the strongest modifier is used, +1 for each additional source. You can change the modifier for multiplier emitters can be modified by changing `MultipleJammerPenalty`.

### ECM Components

To create an ECM  component, define the following effects on a componentDef. You should change the *Description* elements to better match your mod's language and tone.

```json
      {
            "durationData" : {
                "duration": -1,
                "stackLimit": 1
            },
            "targetingData" : {
                "effectTriggerType" : "Passive",
                "specialRules" : "Aura",
                "effectTargetType" : "AlliesWithinRange",
                "range" : 60.0,
                "forcePathRebuild" : false,
                "forceVisRebuild" : false,
                "showInTargetPreview" : false,
                "showInStatusPanel" : false
            },
            "effectType" : "StatisticEffect",
            "Description" :
            {
				"Id" : "LV_ECM_SHIELD_L4",
				"Name" : "Shielded by ECM",
				"Details" : "Applies a +4 penalty to attackers.",
				"Icon" : "uixSvgIcon_status_ECM-missileDef"
            },
            "statisticData" : 
            {
				"statName" : "LV_ECM_SHIELD",
				"operation": "Int_Add",
				"modValue": "4",
				"modType": "System.Int32"
            },
            "nature" : "Buff"
        },
        {
            "durationData" : {
                "duration": -1,
                "stackLimit": -1,
				"uniqueEffectIdStackLimit": 1
            },
            "targetingData" : {
                "effectTriggerType" : "Passive",
                "specialRules" : "Aura",
                "effectTargetType" : "EnemiesWithinRange",
                "range" : 100.0,
                "forcePathRebuild" : false,
                "forceVisRebuild" : true,
                "showInTargetPreview" : false,
                "showInStatusPanel" : false
            },
            "effectType" : "StatisticEffect",
            "Description" :
            {
				"Id" : "LV_ECM_JAM_L3",
				"Name" : "ECM Jammer",
				"Details" : "Reduces target details by -4.",
				"Icon" : "uixSvgIcon_action_sensorlock"
            },
            "statisticData" : 
            {
				"statName" : "LV_ECM_JAMMED",
				"operation": "Int_Add",

				"modValue": "3",
				"modType": "System.Int32"
            },
            "nature" : "Debuff"
        },
```

## Stealth

Thematically Stealth components interferes with an opponent's ability to sensor lock the protected unit. Units absorb sensor waves and thus seem to disappear from the attackers screens. Mechanically it provides a modification to the unit's signature, a modifier to detailed information, and range-based attack modifiers. Because these values aren't set you can use them in a variety of ways, including building stealth true to the table-top version.

Units protected by an active stealth effect will be surrounded by a black bubble when they are visible.

Stealth is defined through a single string that is a compound value:`<signature_modifier>_<details_modifier>_<mediumAttackMod>_<longAttackmod>_<extremeAttackMod>`

* `<signature_modifier>` modifies the unit's signature rating (see above)
* `<details_modifier>` modifies an attacker's electronic warfare check when determining detailed information against the unit
* `<mediumAttackMod>` modifies an attacker's weapons when they are at medium range
* `<longAttackMod>` modifies an attacker's weapons when they are at long range
* `<extremeAttackMod>` modifies an attacker's weapons when they are at extreme range

Finally, units with a Stealth effect cannot be targeted as part of a multi-attack. You should not be able to select them.

### Stealth Example One - Classic Stealth

A stealth effect with values **0.20_4_1_2_3** would have:

 * It's signature value reduced by -0.20, making it harder to detect
 * Apply a -4 penalty to any attacker's detailed information check, making less information available
 * Apply a +1 penalty at the attacker's medium range, making it harder to hit
 * Apply a +2 penalty at the attacker's medium range, making it harder to hit
 * Apply a +3 penalty at the attacker's medium range, making it harder to hit

### Stealth Example Two - Primitive Electronics

Stealth values do not have to be penalties; the code will accept negative values for the effects, making it a net bonus for the attacker. A stealth effect with values **-0.10_-2_-3_-2_-1** would have:

- It's signature value increased by 0.10, making it easier to detect
- Apply a +2 bonus to any attacker's detailed information check, making more information available
- Apply a -3 bonus at the attacker's medium range, making it easier to hit
- Apply a -2 bonus at the attacker's medium range, making it easier to hit
- Apply a -1 bonus at the attacker's medium range, making it easier to hit

### Stealth Components

To create a Stealth component, define the following effects on a componentDef. You should change the *Description* elements to better match your mod's language and tone.

```json
        {
            "durationData" : {
                "duration": -1,
                "stackLimit": 1
            },
            "targetingData" : {
                "effectTriggerType" : "Passive",
                "specialRules" : "NotSet",
                "effectTargetType" : "Creator",
                "range" : 0.0,
                "forcePathRebuild" : false,
                "forceVisRebuild" : true,
                "showInTargetPreview" : true,
                "showInStatusPanel" : true
            },
            "effectType" : "StatisticEffect",
            "Description" :
            {
                "Id" : "LV_Stealth_Armor",
                "Name" : "STEALTH",
                "Details" : "Makes the unit harder to detect and attack",
                "Icon" : "uixSvgIcon_status_ECM-ghost"
            },
            "statisticData" : 
            {
                "statName" : "LV_STEALTH",
                "operation" : "Set",
                "modValue": "0.20_4_1_2_3",
                "modType": "System.String"
            },
            "nature" : "Buff"
        },

```

### Design Note

Stealth closely approximates the sensor and signature spectrum HBS already has in the game. _LowVisibility's_ stealth was created to be less binary than signature reductions. Signature modifiers also hide a target, by reducing the range at which the target can be detected. Sensor modifiers can increase the range, allowing a push and pull between them that mimics TT stealth. However, Stealth reduces the info level (not the range), which allows high-sensor builds to still have a chance to detect them for targeting purposes, without knowing their details.

## Mimetic Armor

Mimetic armor makes the target difficult to visually or impossible to identify, and approximates the chameleonic armor of many sci-fi settings. Mechanically it provides a modification to the unit's visibility as well as an attack modifier based upon how far the unit has moved. Units protected by an active mimetic effect will be surrounded by a shimmer effect when they are visible.

Mimetic armor is defined through a single statistic of type string that is a compound value:`<maxCharges>_<visibilityModPerCharge>_<attackModPerCharge>_<hexesUntilDecay>`

* `<maxCharges>` [int] defines the number of mimetic charges (aka pips) the unit starts the turn with. 
* `<visibilityModPerCharge>` [float] for each charge, the current visibility multiplier of the unit will be reduced by this value. A value of 0.05 with 3 charges would result in the unit's visibility reducing to 0.85 (0.05 x 3 = 0.15). 
* `<attackModPerCharge>` [float] for each charge, attacking units will suffer a penalty equal to this value, rounded up. 
* `<stepsUntilDecay>` [int] defines the number of hexes the unit can move before the visibility and attack modifiers are reduced.

Mimetic effects decay as the unit moves. For each full increment of `<hexesUntilDecay>`, the charges are reduced by 1. In game this is represented by a white eye icon over the in-game representation. Each time the eye icon decreases by one, the visibility and attack modifiers have been reduced.

### Mimetic Example

A mimetic effect with values **4_0.1_1.5_3** reduces their visibility by 0.1 for each point of charge they have remaining. An attack against them suffer a +1 penalty for each point of charge they have remaining. Charges decay by one for every 3 hexes (90m) the target unit moves.

| Hexes Moved | Charges | Visibility Multiplier Mod | Attack Mod |
| -- | -- | -- | -- |
| 0-2 hexes | 4 | 0.60 => 1.0 - (0.1 x 4) | +6 => (4 x 1.5) |
| 3-5 hexes | 3 | 0.70 => 1.0 - (0.1 x 3) | +5 => (3 x 1.5) |
| 6-8 hexes | 2 | 0.80 => 1.0 - (0.1 x 2) | +3 => (2 x 1.5) |
| 9-11 hexes | 1 | 0.90 => 1.0 - (0.1 x 1) | +1 => (1 x 1.5) |
| 11+ hexes | 0 | 1.0 | +0 |
 

### Mimetic Armor Components

To create a Mimetic component, define the following effects on a componentDef. You should change the *Description* elements to better match your mod's language and tone.

```json
         {
            "durationData" : {
                "duration": -1,
                "stackLimit": 1
            },
            "targetingData" : {
                "effectTriggerType" : "Passive",
                "specialRules" : "NotSet",
                "effectTargetType" : "Creator",
                "range" : 0.0,
                "forcePathRebuild" : false,
                "forceVisRebuild" : true,
                "showInTargetPreview" : true,
                "showInStatusPanel" : true
            },
            "effectType" : "StatisticEffect",
            "Description" :
            {
                "Id" : "LV_MIMETIC_3",
                "Name" : "MIMETIC ARMOR",
                "Details" : "Chameleon effect with decaying visibility and attack penalties",
                "Icon" : "uixSvgIcon_status_ECM-ghost"
            },
            "statisticData" : 
            {
                "statName" : "LV_MIMETIC",
                "operation" : "Set",
                "modValue": "4_0.1_1_3",
                "modType": "System.String"
            },
            "nature" : "Buff"
        },      
```

## Narc

Narc beacons launch a small transmitter that attaches to the target and broadcasts their location. Mechanically _LowVisibility_ provides a Narc effect that makes it easier to locate and target the narc'd unit.

Narc effects are defined through a single string that is a compound value:`<signatureMod>_<detailsMod>_<attackMod>`

* `<signatureMod>` defines the visibility modifier applied to the target
* `<detailsMod>` defines the detailed information modifier applied to the target
* `<attackMod>` defines the attack modifier applied to the target

Narc effects are counter-acted by ECM. When a narc'd unit is within a friendly ECM bubble:

* The Narc attack modifier is reduced by the ECM_SHIELD modifier
* The Narc details modifier is reduced by the ECM_SHIELD modifier
* The Narc signature modifier is reduced by the ECM_SHIELD modifier * 0.1

> Example: A narc effect of 1.5_7_-2 would apply the following to the target:
>
>  * A +1.5 signature modifier, making it easier to locate
>  * A +7 detailed information modifier, making it easier to see the internal components of the target
>  * A -2 attack bonus, making it easier to hit the target

### Narc Effect

To create a status effect that applies the _LowVisiblity_ narc logic, use the following declaration:

```json
       {
            "effectType" : "StatisticEffect",
            "Description" :
            {
                "Id" : "LV_NARC",
                "Name" : "NARC TEST",
                "Details" : "You are Narc'd and will be easier to hit and detect.",
                "Icon" : "uixSvgIcon_status_ECM-ghost"
            },
            "statisticData" : 
            {
                "statName" : "LV_NARC",
                "operation": "Set",
                "modValue": "1.5_7_-2",
                "modType": "System.String"
            },
            "nature" : "Buff"
        },
```

Thematically NARC effects should decay after a number of rounds. It's easy to define that with the HBS system, using `durationData` with `ticksOnEndOfRound:true`. 

## TAG

TAG emitters are special sensors that provide deep information on a target so long as they can be targeted with a laser-like beam. _LowVisibility_ provides a TAG effect that makes it easier to locate and target the TAG'd unit. 

TAG effects are defined through a single string that is a compound value:`<signatureMod>_<detailsMod>_<attackMod>`

- `<signatureMod>` defines the visibility modifier applied to the target
- `<detailsMod>` defines the detailed information modifier applied to the target
- `<attackMod>` defines the attack modifier applied to the target

TAG effects are **not** reduced by ECM protection. They are reduced by Mimetic stealth.

### TAG Effect

To create a status effect that applies the _LowVisiblity_ TAG logic, use the following declaration:

```json
        {


            "effectType" : "StatisticEffect",
            "Description" :
            {
                "Id" : "LV_TAG",
                "Name" : "TAG_STRONG",
                "Details" : "Target is TAG'd and easier to hit and detect. Move to break the effect.",
                "Icon" : "uixSvgIcon_status_ECM-ghost"
            },
            "statisticData" : 
            {
                "statName" : "LV_TAG",
                "operation": "Set",
                "modValue": "4.0_8_3",
                "modType": "System.String"
            },
            "nature" : "Buff"
        },
```
Thematically TAG effects should decay after the target moves. It's easy to define that with the HBS system, using `durationData` with `ticksOnMovements:true`. 

## Attack Modifiers
Once a target has been detected it can be attacked normally, though attacks may suffer penalties based upon how strong of a lock they have to the target.

If an attacker only has _sensor lock_ to the target, they suffer a __Sensors Only__ attack penalty of +2 (_SensorsOnlyPenalty_).

If an attacker only has _visual lock_ to the target, they suffer a __Vision Only__ attack penalty based upon their distance to the target. For every 3 hexes away (_VisionOnlyRangeStep_) the attacker suffers a +1 attack penalty (_VisionOnlyPenalty_), regardless of the weapon used.

These penalties described can be adjusted by editing `LowVisibility/mod.json`.

### Zoom Vision

BattleTech has a long standing tradition of zoom vision being a standard feature on cockpits. To support this, components with the `lv-vismode-zoom_mX_sY` tag apply an attack bonus that decays over distance. Each point of X applies as a -1 bonus to the attack roll. For each Y hexes between the attacker and the target, the bonus is reduced by one, until no bonus is provided.

> Example: A unit has a component with tag `lv-vismode-zoom_m3_s8`. For any **ranged** attack between 0-8 hexes, the attacker applies a -3 attack bonus. For attacks between 9-16 hexes, the attacker applies a -2 bonus. At 17-24 hexes the bonus is -1, and at 25+ hexes there is no bonus.

This bonus only applies ranged attacks. This bonus does not stack with other vision bonuses. An attacker with multiple vismode components applies the highest bonus to an attack, plus +1 for each addition vismode that provides a bonus.


### Heat Vision

Like zoom vision, detecting an opponent through thermal vision has been a stable of BattleTech games back to MW2. Components with the `lv-vismode-heat_mX_dY` mimic this effect by applying an attack bonus that increases the as the target heats up. The attacker gains a -X bonus to their attack for each Y points of heat the target currently has. This bonus cannot exceed _HeatVisionMaxBonus_, defined in `LowVisibility/mod.json`.

> Example: A unit has a component with tag `lv-vismode-heat_m1_d20`. For any **ranged** attack where the target has 20 heat or less, the attack gains no bonus. If the target has 20-40 heat the attack has a -1 bonus, for 41-60 heat it has a -2 bonus, and so on.

This bonus only applies ranged attacks. This bonus does not stack with other vision bonuses. An attacker with multiple vismode components applies the highest bonus to an attack, plus +1 for each addition vismode that provides a bonus.

## Miscellaneous

* Units that are a blip cannot be the target of a called shot
* Units that you have no sensor info on cannot be the target of a called shot

# Notes for Mod Authors

HBS has provided an extremely powerful platform that allows you to build complex effects from building blocks like _LowVisibility_ provides. Because this can be overwhelming, here's a few suggestions and reminders that may help when you are designing your mod.

## Spotting and Sensor Ranges

_LowVisibility_ doesn't interfere with the native HBS spotting and sensor range mechanics. If you want equipment to improve the spotting or sensor range, or make a target easier to detect, it's a simple as a modifying already present statistics. For any Mech, Vehicle, or Turret you can set::

* `SpotterDistanceMultiplier` - to multiple any spotting modifiers 
* `SpotterDistanceAbsolute`
* `SpottingVisibilityMultiplier`
* `SpottingVisibilityAbsolute`
* `SensorDistanceMultiplier`
* `SensorDistanceAbsolute`
* `SensorSignatureModifier`

### Sensor Lock Effect

From LA:

```json
 "SensorLockSingleStepEffect": {
      "durationData": {
        "duration": 3,
        "ticksOnEndOfRound": true,
        "stackLimit": 1
      },
      "targetingData": {
        "effectTargetType": "SingleTarget",
        "forceVisRebuild": true
      },
      "effectType": "StatisticEffect",
      "Description": {
        "Id": "AbilityDefT8A",
        "Name": "SENSOR LOCK",
        "Details": "SENSOR LOCK",
        "Icon": "uixSvgIcon_action_sensorlock"
      },
      "statisticData": {
        "statName": "SensorSignatureModifier",
        "operation": "Float_Add",
        "modValue": "2.0",
        "modType": "System.Single"
      },
      "nature": "Debuff"
    },
    "NumSensorLockImpairedEffects": 1,
    "SensorsImpairedEffect": {
      "durationData": {
        "duration": 3,
        "ticksOnActivations": true,
        "useActivationsOfTarget": true,
        "stackLimit": 1
      },
      "targetingData": {
        "effectTargetType": "SingleTarget",
        "showInTargetPreview": false,
        "showInStatusPanel": false,
        "forceVisRebuild": true
      },
      "effectType": "StatisticEffect",
      "Description": {
        "Id": "AbilityDefT8A2",
        "Name": "SENSOR LOCK",
        "Details": "SENSOR LOCK",
        "Icon": "uixSvgIcon_status_sensorsImpaired"
      },
      "nature": "Debuff",
      "statisticData": {
        "statName": "SpottingVisibilityMultiplier",
        "operation": "Float_Add",
        "modValue": "2.0",
        "modType": "System.Single"
      }
    },
    "SensorLockAntiStealthEffect": {
      "durationData": {
        "duration": 1,
        "ticksOnEndOfRound": true,
        "stackLimit": 1

      },
      "targetingData": {
        "effectTargetType": "SingleTarget",
        "forceVisRebuild": true,
        "showInTargetPreview": false,
        "showInStatusPanel": false
      },
      "effectType": "StatisticEffect",
      "Description": {
        "Id": "SensorLockAntiStealthEffect",
        "Name": "SENSOR LOCK: STEALTH SUPPRESSED",
        "Details": "Sensor Lock suppresses Stealth on this unit for 1 Round.",
        "Icon": "uixSvgIcon_status_sensorsImpaired"
      },
      "nature": "Debuff",
      "statisticData": {
        "statName": "LV_PROBE_PING",
        "operation": "Int_Add",
        "modValue": "6",
        "modType": "System.Int32"
      }
    },
```

###
