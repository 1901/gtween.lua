# gtween for Corona

The GTween library, originally created by [Grant Skinner](http://twitter.com/gskinner), ported from ActionScript to Lua for Ansca's Corona SDK by [Josh Tynjala](http://twitter.com/joshtynjala).

## Usage

For those familiar with Corona, usage is very similar to [transition.to()](http://developer.anscamobile.com/reference/index/transitionto), but gtween offers a variety of useful features that go beyond Corona's built-in transitions. If you've used GTween in ActionScript, then gtween.lua should look very familiar.

	local gtween = require("gtween")
	
	local redSquare = display.newRect( 0, 0, 100, 100 )
	redSquare:setFillColor( 255, 0, 0 )
	redSquare.x = 60
	redSquare.y = 60
	
	local blueSquare = display.newRect( 0, 0, 100, 100 )
	blueSquare:setFillColor( 0, 0, 255 )
	blueSquare.x = 170
	blueSquare.y = 60
	blueSquare.alpha = 0
	
	local function redSquareMove_onChange( tween )
		blueSquare.x = redSquare.x + 150
		blueSquare.y = redSquare.y
		blueSquare.alpha = 1 - redSquare.alpha
	end
	
	--[[
		gtween.new
		Parameters:
		1. target
		2. duration in seconds
		3. table of end values
		4. table of gtween properties (separate from tweened values to avoid collisions)
	]]--	
	gtween.new(redSquare, 1.5,
	{
		x = 260,
		y = 260,
		alpha = 0
	},
	{
		transitionEase = easing.outQuad,        -- transition-style easing function
		--ease = gtween.easing.outQuadratic,    -- gtween-style easing function
		repeatCount = math.huge,                -- repeat forever!
		reflect = true,                         -- yoyo
		onChange = redSquareMove_onChange       -- called after every update
	})

## Easing

Corona uses a different signature for its built-in easing functions than the ones that come with gtween, but gtween can use them with the `transitionEase` property (see the example above) to tell gtween.lua to use one of the [easing functions](http://developer.anscamobile.com/content/easing) designed for use with Corona's [transitions](http://developer.anscamobile.com/content/transitions). Use `ease` (same as ActionScript) to use one of gtween's easing functions.

The following easing functions are included in gtween.lua, and should be used with the `ease` property. Some overlap Corona's easing functions, while others are new.

 * `gtween.easing.inBack`
 * `gtween.easing.outBack`
 * `gtween.easing.inOutBack`
 * `gtween.easing.inBounce`
 * `gtween.easing.outBounce`
 * `gtween.easing.inOutBounce`
 * `gtween.easing.inCircular`
 * `gtween.easing.outCircular`
 * `gtween.easing.inOutCircular`
 * `gtween.easing.inCubic`
 * `gtween.easing.outCubic`
 * `gtween.easing.inOutCubic`
 * `gtween.easing.inElastic`
 * `gtween.easing.outElastic`
 * `gtween.easing.inOutElastic`
 * `gtween.easing.inExponential`
 * `gtween.easing.outExponential`
 * `gtween.easing.inOutExponential`
 * `gtween.easing.noneLinear`
 * `gtween.easing.inQuadratic`
 * `gtween.easing.outQuadratic`
 * `gtween.easing.inOutQuadratic`
 * `gtween.easing.inQuartic`
 * `gtween.easing.outQuartic`
 * `gtween.easing.inOutQuartic`
 * `gtween.easing.inQuintic`
 * `gtween.easing.outQuintic`
 * `gtween.easing.inOutQuintic`
 * `gtween.easing.inSine`
 * `gtween.easing.outSine`
 * `gtween.easing.inOutSine`

## Unsupported features

The following features from the original ActionScript GTween are not included in this port. They may or may not be added in the future.

 * GTweenTimeline
 * Plugins