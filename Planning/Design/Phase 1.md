- Top Down (not directly top down, think pokemon-esque)
- 2D Sprites
- Minimal Animation Frames
- Figure out game logic
- Multiplayer? (Hosted on server preferably, but look into p2p)
- Importing Assets
- Hitboxes
- Hurtboxes
- Level Design (Procedural generation/custom maps)

[[Phase 1 Changelog]]
# Settings

Square Size in Pixels:

160px x 160px

# Code Refactors:

## Movement:

```gdscript
extends CharacterBody2D

var screen_size : Vector2
var speed = 5
var direction : Vector2

func _ready():
	screen_size = get_viewport_rect().size
	position = screen_size / 2

func _movement():
	direction = Input.get_vector("left", "right", "up", "down")
	velocity = direction * speed
	position += velocity
	if direction:
		$AnimatedSprite2D.play()
	else:
		$AnimatedSprite2D.stop()

func _spriteDirection():
	if (!$AnimatedSprite2D.flip_h and direction.x < 0):
		$AnimatedSprite2D.flip_h = true
	elif ($AnimatedSprite2D.flip_h and direction.x > 0):
		$AnimatedSprite2D.flip_h = false

func _spriteSelect():
	if direction.y < 0:
		$AnimatedSprite2D.animation = "walk_up"
	elif direction.y > 0:
		$AnimatedSprite2D.animation = "walk_down"
	else:
		$AnimatedSprite2D.animation = "walk_right"

func _physics_process(_delta):
	#limit movement to window size
	position = position.clamp(Vector2.ZERO, screen_size)
	_movement()
	_spriteDirection()
	_spriteSelect()
```

The big deal here is that `Input.getvector()` returns a vector where standing still is {0,0}, moving up would be {0,-1} and moving left or right would be {1,0} or {-1,0} etc you get the point. Adjusting position which is a 2 dimensional vector with this vector multiplied by `delta` is easy and it's easy to influence the direction of the sprites by checking if the X or Y values of `Vector2` is 0 or not. 

`_sprightDirecion` checks the X direction and flips the sprite horizontally if it has not already been flipped. It's important to check if it has or hasn't been flipped to avoid flipping unnecessarily.