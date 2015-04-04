# glsl-combine-smooth

[![stable](http://badges.github.io/stability-badges/dist/stable.svg)](http://github.com/badges/stability-badges)

Smoothly combine two signed distance fields. A useful alternative
to [glsl-smooth-min](https://github.com/stackgl/glsl-smooth-min)
that provides you with an explicit radius of influence and avoids
distorting the distance fields.

**[view demo](http://stack.gl/glsl-combine-smooth/)**

This technique was derived from a
[great talk](https://www.youtube.com/watch?v=s8nFqwOho-s) at
[NVScene](http://nv.scene.org/) by
[Johann Korndörfer](https://twitter.com/cupe_cupe).

## Usage

[![NPM](https://nodei.co/npm/glsl-combine-smooth.png)](https://nodei.co/npm/glsl-combine-smooth/)

### `float combine(float d1, float d2, float radius)`

Given two distances `d1` and `d2`, smoothly merge them together
within the supplied `radius`.

``` glsl
uniform float iGlobalTime;

#pragma glslify: combine = require('glsl-combine-smooth')
#pragma glslify: box     = require('glsl-sdf-box')

vec2 doModel(vec3 p) {
  vec3  off    = sin(0, iGlobalTime, 0);
  float dist1  = box(p, vec3(2.0));
  float dist2  = box(p + off, vec3(1.0));
  float radius = 0.5;

  float dist = combine(dist1, dist2, radius);

  return vec2(dist, 1.0);
}
```

## Contributing

See [stackgl/contributing](https://github.com/stackgl/contributing) for details.

## License

MIT. See [LICENSE.md](http://github.com/stackgl/glsl-combine-smooth/blob/master/LICENSE.md) for details.
