# .o0o.

## 🤩➰➰ virtual moon reverance for global ritual and connection ➰🤩

Immersive moon temple / altar / shrine



### Help!
Water shader doesn't work with 1.1 release

Component and Primitive for the water registered in water.js, called in line 101 of HTML

- Original code by Ada Rode Cannon from https://samsunginter.net/a-frame-components/ < link broken
- Remixed from https://glitch.com/~acute-proximal-dog by Dirk Krause
- Got it from this stackoverflow thread: https://stackoverflow.com/questions/52837505/using-watershader-js-shader-in-aframe




index.html:

    <!-- ☆✼★━━━━━━Water━━━━━━★✼☆｡  -->
    <a-ocean-floor material="normalMap: #moon-texture; sphericalEnvMap: #milky-way;" position="0 -2 0"></a-moon>

    <!-- <a-ocean-plane position="0 .5 0"></a-ocean-plane> -->

    <a-ocean-plane material="normalMap: #water-normal; sphericalEnvMap: #milky-way;" position="0 .5 0"></a-ocean-plane>



water.js:


    AFRAME.registerComponent('wobble-normal', {
    	schema: {},
    	tick: function (t) {
    		if (!this.el.components.material.material.normalMap) return;
    		this.el.components.material.material.normalMap.offset.x += 0.0001 * Math.sin(t/10000);
    		this.el.components.material.material.normalMap.offset.y += 0.0001 * Math.cos(t/8000);
    		this.el.components.material.material.normalScale.x = 0.5 + 0.5 * Math.cos(t/1000);
    		this.el.components.material.material.normalScale.x = 0.5 + 0.5 * Math.sin(t/1200);
    	}
    })

    AFRAME.registerPrimitive('a-ocean-plane', {
    	defaultComponents: {
    		geometry: {
    			primitive: 'plane',
    			height: 5000,
    			width: 5000
    		},
    		rotation: '-90 0 0',
    		material: {
    			shader: 'standard',
    			color: '#8ab39f',
    			metalness: 1,
    			roughness: 0.2,
    normalMap: "src: url(assets/waternormals.jpg)",
    			normalTextureRepeat: '50 50',
    			normalTextureOffset: '0 0',
    			normalScale: '0.5 0.5',
    			opacity: 0.7,
    		},
    		'wobble-normal': {}
    	},
    });


    AFRAME.registerPrimitive('a-ocean-floor', {
    	defaultComponents: {
    		geometry: {
    			primitive: 'plane',
    			height: 5000,
    			width: 5000
    		},
    		rotation: '-90 0 0',
    		material: {
    			shader: 'standard',
    			color: '#8ab39f',
    			metalness: 0,
    			roughness: 0,
    			normalMap: "src: url(assets/moon-texture.jpg)",
    			// normalTextureRepeat: '50 50',
    			// normalTextureOffset: '0 0',
    			// normalScale: '0.5 0.5',
    			opacity: 1
    		},
    	},
    });
