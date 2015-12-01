# css-hexagon
css based hexagon
you can create CSS hexagon this way : https://jtauber.github.io/articles/css-hexagon.html, http://csshexagon.com/ or you can make it little bit more universal.

just edit the dimensions of the wrapping element - MUST BE SQUARE!! 

## See the examples
* [Basic usage](http://drakh.github.io/css-hexagon/examples/basic-usage.html)
* [Shadowed hexagon](http://drakh.github.io/css-hexagon/examples/shadowed.html)
* [Hexagon inside hexagon](http://drakh.github.io/css-hexagon/examples/hexagon-inside-hexagon.html)
* [We must go deeper](http://drakh.github.io/css-hexagon/examples/inception.html)

```html
<div class="wrp">
	<div class="hexagon red">
		<span class="content-wrapper">
			<span class="content">hello</span>
		</span>
	</div>
</div>
<div class="wrp">
	<div class="hexagon white shadow">
		<div class="hexawrp">
			<div class="hexagon red">
				<div class="hexawrp">
					<div class="hexagon white">
						<span class="content-wrapper">
							<span class="content">hello</span>
						</span>
					</div>
				</div>
			</div>
		</div>
	</div>
</div>
```

```scss
$white-color: #fff;
$h-multi: 1.732;
$w-width: 100%;
$wrp-z: 3;
$hexa-width: 86.6%;
$hexa-height: 50%;
$shadow-color: rgba(0, 0, 0, 0.3);
@mixin hexa-warp($curr-w) {
  width: $curr-w;
  height: $curr-w*$h-multi;
  z-index: $wrp-z;
  position: absolute;
  left: (100%-$curr-w)/2;
  top: -36%;
}

@mixin bgcolr($col) {
  background-color: $col;
}

.hexagon {
  position: relative;
  width: $hexa-width;
  height: $hexa-height;
  left: 6.7%;
  top: 25%;
  z-index: 2;

  &:after, &:before {
    position: absolute;
    content: "";
    display: block;
    width: 70.71%;
    height: 122.46%;
    transform-origin: 0 0;
    z-index: 1;
  }
  &:before {
    transform: scale(1, 0.579) translate(70.711356%, -70.711356%) rotate(45deg);
  }
  &:after {
    transform: scale(1, 0.579) translate(70.711356%, 70.711356%) rotate(45deg);
  }
  &.shadow {
    box-shadow: 0px 0px 10px 5px $shadow-color;
  }
  &.shadow:before {
    box-shadow: -9px -9px 10px 3px $shadow-color;
  }
  &.shadow:after {
    box-shadow: 9px 9px 10px 3px $shadow-color;
  }
  &.white, &.white:after, &.white:before {
    @include bgcolr($white-color);
  }
  &.red, &.red:after, &.red:before {
    @include bgcolr(#f00);
  }
  .content-wrapper {
    position: absolute;
    width: 100%;
    height: 100%;
    z-index: 3;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .hexawrp {
    @include hexa-warp(100%);
  }

  .big-hexa {
    @include hexa-warp(80%);
  }
}
```

```css
.hexagon {
  position: relative;
  width: 86.6%;
  height: 50%;
  left: 6.7%;
  top: 25%;
  z-index: 2; }
  .hexagon:after, .hexagon:before {
    position: absolute;
    content: "";
    display: block;
    width: 70.71%;
    height: 122.46%;
    transform-origin: 0 0;
    z-index: 1; }
  .hexagon:before {
    transform: scale(1, 0.579) translate(70.71136%, -70.71136%) rotate(45deg); }
  .hexagon:after {
    transform: scale(1, 0.579) translate(70.71136%, 70.71136%) rotate(45deg); }
  .hexagon.shadow {
    box-shadow: 0px 0px 10px 5px rgba(0, 0, 0, 0.3); }
  .hexagon.shadow:before {
    box-shadow: -9px -9px 10px 3px rgba(0, 0, 0, 0.3); }
  .hexagon.shadow:after {
    box-shadow: 9px 9px 10px 3px rgba(0, 0, 0, 0.3); }
  .hexagon.white, .hexagon.white:after, .hexagon.white:before {
    background-color: #fff; }
  .hexagon.red, .hexagon.red:after, .hexagon.red:before {
    background-color: #f00; }
  .hexagon .content-wrapper {
    position: absolute;
    width: 100%;
    height: 100%;
    z-index: 3;
    display: flex;
    align-items: center;
    justify-content: center; }
  .hexagon .hexawrp {
    width: 100%;
    height: 173.2%;
    z-index: 3;
    position: absolute;
    left: 0%;
    top: -36%; }
  .hexagon .big-hexa {
    width: 80%;
    height: 138.56%;
    z-index: 3;
    position: absolute;
    left: 10%;
    top: -36%; }
```
