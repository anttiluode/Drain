Try it at: 

https://anttiluode.github.io/Drain/

You can change the generating algorithms to things like: 


## Neural Attention Perturbation Variant

```javascript
// The classic drain
let z2c = z.mul(z).add(c);

// Neural Attention Perturbation 
let dir = k1.add(k2).add(k3);
let r = z.mag() * z.mag() + dir.mag();
let phi = 2.0 * dir.arg() + c.arg();
let fs = new Complex(r * Math.cos(phi), r * Math.sin(phi)).add(c);

// THE CLOG: We force a division by zero at the origin
let danger = z.div(c); 

// We add the danger to the attention mechanism
let distorted_fs = fs.add(danger.scale(0.1));

return z2c.scale(1 - lambda).add(distorted_fs.scale(lambda));
```

Ask from your friendly AI for different possibilities. 
