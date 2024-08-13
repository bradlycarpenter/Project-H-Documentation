# Audio

## Footsteps & Sword
```gdscript
func playerAudio():
	if direction and timer.is_stopped():
		footstep_player.pitch_scale = randf_range(0.8, 1.2)
		footstep_player.play()
		timer.start(0.3 * (speed * 0.01))
	if attacking and not sword_sfx_played:
		if not sword_sfx_played:
			sword_sfx.pitch_scale = randf_range(0.8, 1.2)
			sword_sfx.play()
			sword_sfx_played = true
```

- Timer node used to delay the footsteps, speed can be adjusted by changing the multiplier of the `speed` variable.
- Footstep pitch is adjusted every time it is played by using the `randf_range()` function.