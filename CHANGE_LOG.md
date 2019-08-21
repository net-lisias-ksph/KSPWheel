# KSPWheel :: Change Log

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
