# KSPWheel :: Change Log

* 2018-1028: 0.12.10.28 (Shadowmange) for KSP 1.5
	+ Recompile for KSP 1.5+
	+ CHANGE - Add UI toggle to tracks module to allow user-configurable track-texture direction.
	+ CHANGE - Add UI toggle to tracks module to allow for in-editor preview of track rotation/forward direction
	+ CHANGE - Add ability to specify custom friction curve in KSPWheelBase (see included friction adjust patch example)
	+ CHANGE - Add ability to specify wheel collider sweep type in the WHEEL config blocks ('colliderType = RAY/SPHERE/CAPSULE')
	+ FIX - Clean up Dust-Effects related NRE on deleting a part in the editor.
	+ Friction adjustment patch -- affects all wheels; adjust to suit your needs.  Below is a much stickier friction curve than the current defaults.
```
@PART[*]:HAS[@MODULE[KSPWheelBase]]
{
	@MODULE[KSPWheelBase]
	{
		%exSlipPoint = 0.06
		%exSlipVal = 1.0
		%asSlipPoint = 0.35
		%asSlipVal = 1
		%tailSlipVal = 0.6
	}
}
```
* 2018-0410: 0.11.9.27 (Shadowmange) for KSP 1.4.2
	+ FIX - Correct a null-ref in dust-effects code related to loaded but inactive vessels.
	+ CHANGE - Also remove some other debugging logspam.
* 2018-0402: 0.11.8.26 (Shadowmange) for KSP 1.4.2
	+ Update and recompile for KSP 1.4.2
	+ CHANGE - Add new dust-effects system, using the new Shuriken particle system from Unity.
		- Entirely new particle effects, new textures, and new code.
		- Implementation is very basic and will be improved in future releases (more options, better default configuration)
* 2018-0321: 0.11.7.25 (Shadowmange) for KSP 141
	+ Recompile for KSP 141
	+ Disable Dust-effects entirely at the plugin level.
* 2018-0310: 0.11.6.24 (Shadowmange) for KSP 1.4
	+ MAJOR CHANGE - Update for KSP 1.4
	+ FIX - Dust color camera now uses all pixels from sampled texture rather than just a single pixel.
* 2018-0121: 0.10.5.23 (Shadowmange) for KSP 1.3.1
	+ FIX - Wheels with motors will now satisfy the stock 'must be on motorized wheels' contract objective for base construction.
* 2017-1231: 0.10.5.22 (Shadowmange) for KSP 1.3.1
	+ CHANGE - Add Max EC/s display to motor module in editor.
	+ CHANGE - Add a module that can manage UI state for multiple motor modules
	+ CHANGE - Add capability to steering module to only turn the visible mesh (disables wheel internal steering)
	+ CHANGE - Add a module that can remove animations from parts
	+ CHANGE - Add a module that can play animations at a speed linked to wheel speed
* 2017-1008: 0.10.5.21 (Shadowmange) for KSP 1.3.1
	+ Recompile for KSP 1.3.1
* 2017-0904: 0.9.5.20 (Shadowmange) for KSP 1.3
	+ FIX - Bouncing upon landing -- springs now use a purely linear response model.
	+ FIX - Vessel landed-at state detection if the bump-stop collider contacts the ground
* 2017-0829: 0.9.5.19 (Shadowmange) for KSP 1.3
	+ FIX - Nullref/spam if launching an aircraft with gear deployed.
	+ FIX - Also cleans up action-group initial-state setting/updating from gear states.
* 2017-0826: 0.9.5.18 (Shadowmange) for KSP 1.3
	+ FIX - Null-ref on animations in the editor for ALG parts.
	+ FIX - FAR voxelization issues for ALG parts and other KSPWheel parts in general.
	+ FIX - Gear Action-group state initial setup for ALG parts.
	+ FIX - Drag-cube updating for ALG parts.
	+ FIX - Ignore trigger colliders during suspension sweeps.
* 2017-0715: 0.9.5.17 (Shadowmange) for KSP 1.3
	+ FIX - KSPWheelDamage module now uses fixed-delta time/time warp multipliers to calculate damage-from-speed.  Should resolve issues of wheels breaking on craft while in orbit.
	+ FIX - KSPWheelBase now disabled wheel updates when in 'HIGH' timewarp mode (non-physics warp).  Should resolve issues of wheels breaking during timewarp (they were colliding with other parts in the same vessel).
	+ FIX - Animation time queries for inverted animations (retract style animations, rather than the officially supported deploy style).  Should clean up problems of offset suspension positioning.  Might still have issues/have created other issues....
	+ FIX - Scale slider being visible in flight scene
	+ CHANGE - Add capability to adjust friction multipliers from in-game, both globally and per-part (multiplicative).
		- Global settings are accessed from the in-game difficulty->KSPWheel settings menu.
		- Per-part settings must first be activated/enabled from the in-game difficulty->KSPWheel settings menu.
* 2017-0604: 0.9.5.16 (Shadowmange) for KSP 1.3
	+ Recompile for KSP 1.3
	+ CHANGE- add capability to set min/max for spring-rating slider through config in KSPWheelBase
		- minSpringRating = 0.2
		- maxSpringRating = 0.8
	+ CHANGE - add per-module config fields to hide various GUI elements for the common/major modules
* 2017-0319: 0.9.4.15 (Shadowmange) for KSP 1.2.2
	+ FIX - Error in water propulsion module that would cause lack of thrust output in multi-wheel parts, as well as causing loss of dust-effects upon transition back to land.
	+ FIX - Sided model handling leaving part unable to surface attach.
	+ FIX - Landed biome detection/updates not working properly, giving incorrect science experiment results.
	+ FIX - Update the 'wheel state' persistence string immediately on state changes -- should enable greater level of interaction with external mods using the PartModule.Fields[xxxx] interface.
	+ FIX - Suspension display position in editor being incorrect on scaled models.
	+ CHANGE - Add ability to specify the name used in action group and UI-buttons for wheel deployment module.  'actionName = XXXX'
	+ CHANGE - Add the motor stats displays to those that are shown/hidden by the show/hide wheel controls button.
	+ CHANGE - Add ability to specify min and max gear ratios in the motor/tracks module config ('minGearRatio / maxGearRatio = XXX')
	+ CHANGE - Add API accessible max-EC-per-second field to motor module, for ease of compatibility with BonVoyage
	+ (field = maxECDraw, float, non-configurable, for interop use only)
		- CHANGE - Add action group toggles for:
			- Motor Lock
			- Motor Invert
			- Tank Steering Lock
			- Tank Steering Invert
			- Steering Lock
			- Steering Invert
			- Suspension Lock (landing legs)
* 2017-0305: 0.9.4.14 (Shadowmange) for KSP 1.2.2
	+ FIX - Move vessel-debug GUI code out of vessel-module, should result in a minor performance gain with many unloaded vessels in play.
	+ FIX - Move dust-camera code into a single-instance setup; only a single camera exists that is shared for all vessels.  Should result in minor performance gains with many unloaded vessels in play.
	+ FIX - Repulsors should no longer temporarily initialize to 'on' when craft is reloaded.
	+ FIX - Incorrect water-effects for repulsors
	+ FIX - NaN related crashes in the Advanced Damage Model code
	+ FIX - Null-ref/IndexOOB in tracks module when loading a part without Skinned-mesh renderers on it.
	+ FIX - Incorrect double application of 'suspensionOffset' when wheel was in broken state.
	+ FIX - Incorrect calculation of rolling resistance, especially on small wheels
	+ FIX - Rework 'locked-suspension' code to work more appropriately.
	+ CHANGE - New feature - Anti-Roll.  Only works on wheels placed in symmetry.  (WIP)  Currently part of the KSPWheelBase module but may be moved into a secondary module in the future.
	+ CHANGE - Allow suspension module to specify secondary wheel indexes from which compression for the visible suspension will be averaged.
	+ CHANGE - KSPWheelDeployment - Rework how 'temp collider' is setup.  This transform should now be positioned in the model hierarchy underneath the suspension transform, and should retract with the rest of the wheel.  Offset and offset axis can now be specified in the config.
		- WARNING - Might impact other mods that are using the wheel deployment module.  The configs for deployable parts may need to be updated prior to being compatible with this version of KSPWheel
* 2017-0225: 0.9.3.13 (Shadowmange) for KSP 1.2.2
	+ FIX - Null-ref in motor module caused by incorrect update ordering
	+ FIX - Motor limiter not being applied to motor output.
	+ FIX - Repulsor power state for UI button not being persistent.  Fixes repulsor power state not being adjustable in the editor.
	+ FIX - Use velocity of hit-collider when determining wheel velocity.  Helps reduce problems of vehicles sliding when being transported on top of other vehicles; but does not completely fix it.
	+ FIX - Max driven speed not being updated on gear and/or scale changes in the editor.  One of the fixes for this may have also fixed up a few other wheel-group related updating issues in the editor.
	+ FIX - Miscalculation of max safe speed that did not include part rescale factor (used in some tracks and stock parts).  Fixes scale-related cases of the motor being able to drive a part past its max safe speed.
	+ FIX - ALG parts now update their drag cubes based on deployment state.  Also much less draggy in general.
	+ CHANGE - Tank-steering equipped parts will now also use brake input to assist in steering, especially at higher speeds.  Overall steering response greatly improved.  Will refine this a bit in the next release with an input curve and/or limiting sliders.
	+ CHANGE - Add 'debug-rendering' to vessel-debug module.  Enables some line-renderers for the wheel axis' and wheel circle.  Should aid in debugging of rigging / positioning.
	+ CHANGE - Add action group support for repulsor power state, and 5 height presets (20%, 40%, 60%, 80%, 100%).
	+ UPDATED MODULE - KSPWheelAdjustableGear - Rewritten for new model rigging and suspension operation.  Should be much more stable.
		- WARNING Existing craft with ALG parts might not restore properly.  Wheels may be misaligned and need to be re-setup in the editor.
		- Now includes deploy and retract sound effects (stock landing gear sounds)
	+ NEW MODULE - KSPWheelConstraints - Does what it says... (but more configurable and compatible than stock constraints modules)
	+ NEW MODULE - KSPWheelWaterPropulsion - Allows for wheels and/or tracks to output propulsive force when partially submerged.  Includes new water dust effects handling for propulsive wheels/tracks.  Module must be added to the part, so will only be enabled on specific parts.
	+ CHANGE - First pass implementation of 'advanced' damage model.  In this model persistent wear accumulates on the parts based on their use.  Functions in addition to the simple damage model.  Has three main components, some of which may only be applicable to specific wheels.  Each component may be enabled or adjusted through the in-game difficulty settings menu (Settings->Difficulty->KSPWheels -> Damage Model).
		- Speed - Close to and over max-speed -- persistent increased rolling resistance.  Simulates additional 'drag' due to degradation of wheel material and bearings.
		- Load - Overloading and hard impacts reduce maximum spring output permanently (until repaired).
		- Heat - Electric motors output heat relative to the difference between their input and output power (momentary efficiency).  Heat beyond a specific point in the part will accumulate damage in the motor that reduces its max efficiency and max RPM.  Heat can be managed through standard KSP heat management mechanisms.
* 2017-0212: 0.9.3.12 (Shadowmange) for KSP 1.2.2 PRE-RELEASE
	+ MAJOR CHANGE - Updated motor mechanics.  Use proper math to derive input power from the torque and efficiency stats for the motor.
		- Adds a new config file to define an EC->kJ conversion factor.  Defaults to 1EC = 65kJ, which is what the stock wheel motors use.
	+ CHANGE - Add additional steering controls for 'high-speed-steering-limit' and 'steering-response'.
	+ CHANGE - Add configurable fwd and side friction to KSPWheelBase.  Will be used to increase the friction of tracks in a future KF release.
	+ CHANGE - Rework dust-effects power/speed/energy/emission handling to make them more consistent across various wheels, loads, and scales.
	+ CHANGE - New repulsor water-effects mode.  Uses a secondary emitter with different parameters and coloring.
	+ FIX - Dust-particles being offset by Krakensbane origin shifting.  Now update the particle positions when the origin shifts.
	+ CHANGE - Change the default damper ratio adjustment range to be 0.35 <-> 1.0
	+ CHANGE - Add 'index-in-duplicates' support to wheel modules.   Allows for part-welding using existing wheel models.
		- WIP -- works, but may need additional development/fixes for some uses and setups.
		- NOTE: Will need a new/updated constraints system as the stock one falls on its face in this scenario (cannot properly handle multiple same-named transforms)
* 2017-0205: 0.9.2.11 (Shadowmange) for KSP 1.2.2
	+ CHANGE - Add in-game setting to adjust dust overall output
	+ CHANGE - Rework ALG deploy/retract animation to eliminate visible clipping
	+ CHANGE - Steering curve uses vessel velocity rather than wheel velocity (slip no longer reduces steering)
	+ CHANGE - Adjust sound handling for motor and speed setups
	+ CHANGE - Adjust sound handling for lateral slip
	+ CHANGE - Update suspension calculations to include tracks 'load share' specification.  Should reduce jitter/bounce on tracks and give them generally better default setups.
	+ CHANGE - Fix wheel damage calculation for stress - is now proportional to load/maxLoad rather than linear with over-loading.  Should remove the difference between calculation on large and small wheels.
	+ CHANGE - Fix Sound effects continuing when wheels are broken/retracted/etc
	+ CHANGE - Fix track textures continuing to update even when broken
	+ CHANGE - Set rigidbody to first one found upward in hierarchy.  Should solve problems of wheels not working when attached to physics-less parts.
	+ CHANGE - Add an 'allowScaling' field to base module, defaults to true.  If set to false disables -all- model scale handling code and force-sets the lookup value for scaling to 1 (used for damage, speed, etc).
	+ CHANGE - Add optional 'scalingTransform' to config of base module.  If that field is populated only the single specified transform will have model scaling applied to it.  If field is not populated defaults to the existing behavior of scaling all models.
	+ FIX - Overriding of default deploy state in config not working on root parts (stock bugs)
	+ CHANGE - Add optional specification for suspension compression state for use with animations.
	+ FIX - ALG gear will now set the gear-action group state if they are deployed.
	+ CHANGE - ALG - Add 'Align Wheel To Ground' button.  Does what it says on the label...
	+ FIX - Repulsor handling near and under the surface of water.  All cases should now have a defined behavior and none should result in any surprising forces on the craft.  Repulsors can now push an underwater craft upwards towards the surface, and smoothly transition up to normal operation once above the water.
	+ CHANGE - Add repulsor sound effects - they currently depend on loading/ec-use, and are unclamped, so may be -loud- under extreme loads (50t+) for a single repulsor.
	+ CHANGE - Add brakes to action groups; reassignable.
		- NOTE - Dust power was incorrectly default to zero in the configs with this release.  Will return to default of 1 in future releases.  To enable dust effects, go into the in-game settings, KSPWheel tab, and set the Dust Effects Power to >0.
* 2017-0128: 0.9.2.10 (Shadowmange) for KSP 1.2.2
	+ Fix the difficulty / game-settings sliders to have decimal increments.  Scale and damage values may now be specified with non-integer values.
	+ Fix tank-steering enabled parts ignoring the steering and motor lock states.
	+ New spring auto-calculation method using a more configurable setup.  Also cleans up the problems brought on by the integral values which could cause improper spring calculation for wheels that had been over-compressed at any point.
		- Makes it much easier to land aircraft as the spring force no longer drops off when below <0.5 compression (until ~0.8).
		- Much larger stable range of linear spring response.  Spring only uses curves at the extremities, mostly to help prevent over-compression.
		- Use length-corrected mass to calculate spring force -- should be consistent at all scales and suspension travel lengths.
	+ Fix drag cubes for scaled wheel parts.  They are now updated manually in flight scene for the new part scale.
	+ Fix ALG doors not lining up properly when placed in symmetry, also properly set the strut and wheel angle when symmetry is enabled.
	+ Fix ALG adjustments both being called 'strut'.  One of them now specifies that it adjusts the wheel.
	+ Increase the base durability factor of all wheels by 4x for impacts.  This doesn't impact their load-rating, which is the determining factor for actual impact rating, but it allows them to absorb much more force relative to that load rating.
	+ Fix FAR incompatibilities, as near as I can tell.  Might be some issues with the colliders that can and will be cleaned up in the near future.
		- As a bonus wheels can now actually explode and are no longer indestructible.
* 2017-0122: 0.9.2.9 (Shadowmange) for KSP 1.2.2
	+ Add dust effects handling -- use either camera or config/biome based color setups.  WIP implementation of water handling.
	+ Update repulsor handling code - offset force application point to the wheel collider itself.
	+ Add Adustable-landing-gear handling module
	+ Suspension animation now displays 50% compression in editor
	+ Tank steering now respects motor lock and steering lock toggles
	+ Add .version file for CKAN support
	+ More detailed patch notes to come later....
* 2017-0115: 0.9.2.8 (Shadowmange) for KSP 1.2.2 PRE-RELEASE
	+ IMPORTANT
		- Completely remove any previous versions of KSPWheel before installing this update.
	+ Wheel Collider
		- Only apply AG fix when brakes are on and motor torque < brake torque.
	+ Part Modules
		- Add WIP scaling support.  Basic functionality is in place but certainly not balanced yet.
		- Add WIP wheel-group support.  Currently it will update most motor, steering, suspension, brakes, and repulsor stats for wheels with shared group.  The default wheel group of '0' means 'no group', so group must be set to 1 or greater to enable the wheel-group feature.
		- Add multiple damage types, add settings option to switch between them.  Default = simple.  Options = none, simple, advanced.  (advanced implementation WIP)
			- In simple mode the current wheel RPM is checked vs. max vehicle speed, excess speed for an extended duration will break the wheel.  Wheel stress is also taken into consideration -- overloaded vehicles or large impacts can break the wheel.
			- Currently any crew member can repair a wheel.
		- Complete rework of motor mechanics.  Include switching of gear ratios, and entirely new power calculation methods.
			- Temporarily add motor substep integration to help decrease problems of motor over-torque in a single physics frame.
		- Rework tracks module to derive from motor module for easier integration of track motor/torque functions and cleaner part configs.
		- Complete rework of tracks motor-torque input calculations.  Now keep all wheels at the same linear velocity while maintaining constant energy in the system.
		- Add max speed specification to base module, used for steering and damage calcs
		- Add default steering curve based on config-specified max speed for the part.
		- Add half-track steering mode for tank-steering type wheels.  This inverts the tank-steering motor input when in reverse.
		- Rework debug module -- now uses a custom GUI and displays data for all wheels on a part.
		- Clean up default ignored layers to include transparentFX
		- Save and load persistent data on a per-wheel basis, includes rpm and suspension parameters
		- Add rolling resistance as a config field to base module
		- Add correction for gravity into auto-spring calculations
		- Add basic GetInfo() data to most of the modules.
		- Remove KF part configs
		- Remove module-manager as it is no longer needed.
* 2017-0107: 0.9.1.7 (Shadowmange) for KSP 1.2.2 PRE-RELEASE
	+ Part Modules
		- Add a KSPWheel game-settings menu.  Currently only has a single functional setting (advanced mode), more will be added in time.
		- Add a new suspension auto-tuning method.  Enabled by default, can be changed in the stock in-game settings menu by setting 'advanced mode' to off.  Works well as-is, but will see further tuning after more testing.  Might not properly calculate spring strength on low-gravity worlds, may need to adjust the spring-rating slider to compensate.
			- Only damper ratio and a basic spring-strength control are available in basic mode.  The actual spring strength used will be adjusted based on vehicle mass and spring compression.  Might have harmonic interference/bouncing in some scenarios or setups;  please report any problems regarding suspension tuning along with relevant details so that
			- Advanced mode is equivalent to the old manual mode; you must specify load rating, ride height, and damper ratio properly for the craft and intended uses.
		- Add a UI button on wheel parts that will show/hide all other wheel related UI controls.
	+ Wheel Colliders
		- No Changes
* 2016-1218: 0.9.0.6 (Shadowmange) for KSP 1.2.2 PRE-RELEASE
	+ Update to GPL license.
	+ Re-add KF configs, but adjust to patch existing parts in-place rather than create duplicates.
* 2016-1210: 0.9.1.5 (Shadowmange) for KSP 1.2.2 PRE-RELEASE
	+ Initial repackage as simple API / .dll
	+ See wiki for documentation on how to use the KSPWheelCollider.
