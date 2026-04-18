Try it at: 

https://anttiluode.github.io/Drain/

You can change the generating algorithms to things like: 


## Neural Attention Perturbation Variants

```javascript
// Flip the spin (Complex Conjugate)
let z_conj = new Complex(z.re, -z.im);

// The Tricorn Fractal equation
let tricorn = z_conj.mul(z_conj).add(c);

// Neural Attention
let dir = k1.add(k2).add(k3);
let r = z.mag() * z.mag() + dir.mag();
let phi = 2.0 * dir.arg() + c.arg();
let fs = new Complex(r * Math.cos(phi), r * Math.sin(phi)).add(c);

return tricorn.scale(1 - lambda).add(fs.scale(lambda));
```

Magnetic Dipoles: 

```javascript
// Magnet Phase Transition Equation: ((z^2 + c - 1) / (2z + c - 2))^2
let z2 = z.mul(z);
let top = z2.add(c).sub(new Complex(1, 0));
let bot = z.scale(2).add(c).sub(new Complex(2, 0));

// We must catch the division by zero (the clog)
let magnet;
if (bot.mag() === 0) {
    magnet = new Complex(NaN, NaN);
} else {
    let div = top.div(bot);
    magnet = div.mul(div);
}

// Neural Attention
let dir = k1.add(k2).add(k3);
let r = z.mag() * z.mag() + dir.mag();
let phi = 2.0 * dir.arg() + c.arg();
let fs = new Complex(r * Math.cos(phi), r * Math.sin(phi)).add(c);

return magnet.scale(1 - lambda).add(fs.scale(lambda));
```

Burning Ship
```javascript
let z_abs = new Complex(Math.abs(z.re), Math.abs(z.im));
let burning_ship = z_abs.mul(z_abs).add(c);

// Neural Attention
let dir = k1.add(k2).add(k3);
let r = z.mag() * z.mag() + dir.mag();
let phi = 2.0 * dir.arg() + c.arg();
let fs = new Complex(r * Math.cos(phi), r * Math.sin(phi)).add(c);

return burning_ship.scale(1 - lambda).add(fs.scale(lambda));
```

Etc
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
