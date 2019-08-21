# KSPWheel :: Change Log

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
