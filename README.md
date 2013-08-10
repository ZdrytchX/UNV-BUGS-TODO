UNV-BUGS-TODO
=============

Contains a list of TODOs and Bugs

From now, I'll just edit this document via browser.

This is a list of stuff that ZdrytchX wants changed, personal wanted features/removal and/or actual exploits/bugs etc.
I will do my best not to repeat a bug in multiple  categories by the way.

****MISSING FEATURES/FIXES FROM GPP
-/memo command (It's like granger's !note command, tells the player that he has a
  message as he connects to the game if he's not there, but doesn't give the message
    right away until he does /memo read <memo#> and can list memos by their number identification)
-Model displacements not fixed (was fixed in early standalone gpp but NOT tremfusion)
-projectile lag compensation doesn't work for me personally, no matter what cG_projectilenudge
  or cg_unlagged is set to
-Building in Doorways

****GPP-ONLY FAULTS (doesn't exist in 1.1, exists in unvanquished though)
-Projectiles don't deal locational Damage
-Damage to players/buildables don't produce any weapon-specific particle systems, only bleed
  (although vs players, it only produced blood for non-killing projectiles and hitscan in 1.1)
-Creeps goes through walls (did in 1.1, but only to a certain extent, and 1.1 was more realistic in this matter)

Exploits:
-Flamer
  -Due to the repeat rate of 200msec, the gap between each "missile" is humoungous, a dretch can get
  through a flame without getting hurt
-Spawning gives ~100-200 msec (is it the weapon-up time?) "paralised animation" time (i.e. aliens float above the egg before spawning,
  humans load their gun) which actually helps spawn campers
-Biting/Slicing through narrow areas (i.e. cages) - due to the "wall-player" priority detection
  (in 1.1, if you aim at a player, but a wall is closer than them and is within range of the claw,
  it hits the wall only)

****1.1-ONLY FAULTS (doesn't exist in GPP, *may* exist in UNV, so low priority)
-Projectiles capabable of dealing splash damage don't deal locational damage

****BOTH GPP/1.1 FAULTS (For more, see ****OTHER)
-PERS_HITS unused (hence if impure, it allows me to use cg_hitsounds on an impure client)

****CLASSES
=Granger
  -Falldamage doesn't trigger when using wallwalk
=Basilisk
  -Gas effect restarts whenever re-gassed rather than just re-increasing intensity
  -Gas "trace" function seems to return true within range despite of walls
=Marauder
  -"wallclimbing" walljumping bug is actually caused by velocity clipping
    (also happens in 1.1, however it stopped the clipping just before it jumps again)
  -Due to the velocity clipping, if you land before you can jump for some reason, the walljump
    velocity cap takes place, and you slide without being able to jump, feels horrid
=Dragoon
  -ADV goon pounce timer is triggered by all weapons (i.e. Snipe, then pounce, the pounce
    deals 0 damage
  -Headshots are now impossible (non-locational damage)
  -Pouncing onto a human's head makes you paralised (wasn't this fixed in gpp?)
=Tyrant
  -Tyrant charge deals practically no damage near the end of the charge,
    and only hinders the player, please add something like a constant to
    add to the charge damage, or increase the threshold to cancel out the
    charge at a certain point, to allow swiping (and jumping)

=Human_base
  -Velocity clipping with dodge timer, see marauder's "wallclimbing"
    (instead of a jump timer, this one uses the anti-dodge spamming timer).
    This one isn't urgent since dodge was removed.
  -Jumping while in forced crouch position is possible, and bunnyhopping while doing so
    allows you to abuse this and travel fast in vents

****WEAPONS
=Lcannon
  -can be refilled while charging without losing charge
  -Balance wise, I want the charge-up time to be 2.5 seconds. Works well with my 1.1 mod.
    It will also help tackle the "charging: swipe swipe swipe swipe *dead before finish charging*" issue
  -Balance wise, I want it to deal less self-damage to encourage luci jumping, because
    unvanquished/gpp gameplay with luci feels horribly slow for me.

****BUILDABLES
HUMANS
=MGturret
  -Silly spinup time, please actually code the spinup properly. Its retarded when we have a barrel
    that spins with momentum.
  -Shoots minimum 30 degrees (normal) but still tries to fire if the enemy is between 30 and 45 degrees
=DCC
  -DC farming for near-instant healing - You might want to fix this for high-bp servers, let's say
    capped at 10 DCs per buildable
=Drills
  -They are highly FPS-dependant for jumping, with my FPS I often can't jump on them, but sometimes
    I can.
=Tesla Gens
  -Don't give them the fat model. I love the current ones how they can fit in tight places.
=Repeaters
  -Please, don't use a tall model. (You said you might use that conncept art for the repeater)
    What I like about the repeater - Deals high splash damage, Low health, Small and compact (fits in small places)

ALIENS
=Hives
  -Doesn't target attacker from any distance, unlike GPP (See gpp-missing features at top)
=Tubes
  -They don't hide well with their colour.
  -Although the models do shift to the bboxes, they can't squeeze themselves into horizontally-tight
    places
  -Are their eyes useful? How do they see from their arses? Why don't they aim at far humans? :P
  -take a crapload of renderer fps, even if not firing
  
****PHYSICS
-Velocities are snapped onto integer values (cannot travel at 0.9 units/s for example)

****HUD
-Minimap is covered by fps/lagometer/timer etc. on some resolutions
-Scoreboards don't scroll
-Scoreboards don't stretch with the resolution
-Atube particle systems makes people lag like shit when you're close to one. It's probably better
  to make the atube shoot gas bombs with smaller trails behind them, representing acideous gas

****Particle Systems
-Flamer's "x/y" velocity pushes it to one side of the map rather than one side of the viewer,
  and so on one angle it's correct while on another angle it misses the crosshair completely
-Flamer's system is split into three seperate emitters, and hence can be emit through walls.

****OTHER
-s_useOpenAl prevents compiling videos with sound
-OpenAL is shit, it ruins sound quality, and makes things hear-able from other side of the map
-Unvanquished's /video does not compile with gamma and sound, like as if it's using 1.1
  renderer to compile them
-Some guns don't have imapct sounds. Trust me, they sound more awsome when they do have them.
-cg_drawbbox doesn't addjust for changing bbox sizes (i.e. crouching, ducking cade)
-When things get rendered behind walls, you can sorta see a healthbar pop up and then disappear like
  as if you're peering around the corner
-Stuff gets renderee behind walls, it was a crapload better in tremulous. Either add a cvar or
  find a new way.
-Shadows of entities don't get rendered if their center point isn't in the FOV
-Demos record the 'confirmed packets' that the server sends and the client receives,
  not what the actually client sees (includes client-prediction positions). This makes
  the demo seem 'lagged behind'

****EXPLOITS (I don't really have a problem with some of these, but they are worth mentioning I guess)
-Strafe Jumping
-Zapping underwater
-Jetpack underwater
-Unlagged fails to detect connection speed inconsistancies (i.e. my connection TO america is
  faster than FROM america, so my TO connection latency is actually smaller than my FROM latency
  and I have to aim BEHIND about 90 msec, where on europe it's the opposite. My polation-o-meter
  "hack" actually helps me counter this for impure servers in 1.1., see FEATURE REQUEST)
-Since range is determined from centerpoint of player, things like the reactor deals huge amounts
  of damage in certain places but nothing in other places
-Projectiles don't deal knockback in relation to themselves like Q3:A did with direct-hits

****NON-EXPLOITED BUGS (some can be exploited, but isn't common)
-Jetpack "hover" verticle speeds doesn't reach 0 for velocity floating number division reasons
-cg_thirdpersonshoulderviewmode has to be "2" to be actually enabled, (1 = 0 = anything except 2)
-Unlagged fails to calculate porperly on moving platforms because it doesn't track back entities
-Rotating entities effect player's aim wrongly when wallwalking (i.e. on ceiling, pushed by a
  clock-wise rotating entity is supposed to to make them rotate anticlockwise in the player's view
  but rotates them clockwise (problem: reaching impossible "1" degree angle (below 89, above 89)
-When touching a bbox of another player, jumping isn't played until the server confirms it (making
  client-prediction errors)
-Wth happened to Newton's Physics? (TremZ project, referring to Dusshan... uhh forgot his name)
-FPS inconsistancies when moving around with a crapload of buildables nearby
-Medistats heal through walls, as long as human's above its vicinity
-Players can cause grief to high-ping players by getting near them, causing client-game prediction
  errors (i.e. painsaw vs dragoon)
-Step-up is possible from any upward velocity
-Unlagged fails to counter for connection inconsistancies
-Bboxes aren't inline with underwater swimming (not checked with new UnvGuy)
-Teleporters provide exactly 400 ups, nothing else

****BOTS for Fuma-chan <3(fuma's a girl's name, isn't it?)
**BUGS/Exploits
-Predictable
**Feature Requests
-Have paths editable in-game so you can install "one-way shortcuts" (i.e. have a player jump off
  certain ledges to continue chasing)
-Use unlagged to track back players, then get the bot to aim at that, track forward players again,
  then use aiming extrapolation that's used for projectiles for non-hacky aim (it's weakness is
  side-to-side strafing aliens though, but you can use aiming delay to counter for that anyway)

****FEATURE REQUEST
-Re-add trem 1.1 style thirdperson, with cg_thirdpersonheight cvar
-Make cg_projectilenudge:
  Set 1: not effect first-person driven missiles if unlagged is disabled.
  Set 2: Effect first-person projectiles despite lagged/unlagged
  Set 3:Set 1 + Make particles destroy themselves upon contact instead of waiting for confirmation of hit
  Set 4:!Set 1 + set3
  set 5:etc.
  ...
  Set >7:Set 1 + Set value for ping, so your nudge isn't forced to "assumed ping". (I get projectiles
    hitting players then turns out they never hit a lot)
-Add cg_thirdpersonheight (constant) so you don't have to look at the human's silly neck
-Wallwalk on entities
-Decolourise speedometer graph option (>8 until value = 16?), it's impossible to read as an alien at high velocities
-Having mass driver shoot through multiple targets
-Damage-dependant luci radius
-Polation-O-Meter - Shows extra/interpolation status with numbers
  [https://fbcdn-sphotos-g-a.akamaihd.net/hphotos-ak-ash3/q80/s720x720/1004496_10201624562837291_31056923_n.jpg]
-Accelerometer - Shows change in velocity (per second) between frame rates
-cGaz's strafe/race hud capability? :O
-Nerf Dragoon's pounce, viech, you've done the balancing wrong. You balance them completely the wrong way.
-Buff tyrant's repeat rate from 300msec to 150msec, and increase velicity to 2.5x. Works with my mod well.
  The tyrant charge in KoRx is 56 dmg only, but the rest follow GPP's value and is not OP at all. In fact,
  you can barely kill a bsuit with one full charge.
-A new solution for basilisks' "ping-dependant performance" (easiest to escape and grab victims if low ping
  since it isn't unlagged, if it were unlagged it'll cause client-game prediction issues as well)
-Split console into three parts: MODs, Messages, IRC. Navigated similarly to the linux consoles (text can be clicked)
-Predict buildable-dealt knockback (i.e. teslas, often I can get into the human base without receiving knockback
  from teslas, and try to bite a human but then gets warped outside the base and dies)
-/allstats, /mystats, teamstats
-Allow aliens to evolve with humans nearby (sixthly tried with his aussieassault 1.1 server, but failed)
-Sixthly's AA Map Rotation Vote menus, or similar
-Buy medkit from armoury
-Make alien buildable creeps (that slow humans) non-buildable zones for humans, i.e. prevent tesla-egg camping
-Make alien claws multi-hit-able
-Make marauder's jump timer only apply for non-walkable surfaces (i.e. walls, not ground)
-Soften the marauder's velocity cap effects (i.e. make the marauer only kill [(velocity-cap)/90]
  of its velocity rather than a hard-limit)
-Centered Weapon View option
