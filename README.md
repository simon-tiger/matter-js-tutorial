# matter.js Tutorial
Welcome to the matter.js tutorial!
matter.js is a physics engine for JavaScript.

## Getting Started
You have 2 ways of getting started:

* You can reference matter.js with a CDN:
  
  ```html
  <script src="https://cdnjs.cloudflare.com/ajax/libs/matter-js/0.12.0/matter.js"></script>
  ```

* You can download the [edge build](https://github.com/liabru/matter-js/blob/master/build/matter.js) and reference it:
  
  ```html
  <script src="matter.js"></script>
  ```

Next, create a world.
In your JavaScript, create a world using the following syntax:
```javascript
var Engine = Matter.Engine;

var engine = Engine.create();
var world = engine.world;
```
The engine is basically the thing that's going to move all of the stuff into the physics world.

### Bodies
matter.js uses this concept of a `Body`, to put things in the physics world.
To create one, In your JavaScript, use the following syntax:
```javascript
var World = Matter.World,
    Bodies = Matter.Bodies;

var particle = Bodies.circle(400, 60, 40);

World.add(world, particle);
```

### Running Everything
After creating all of the bodies, we have to run everything using the following syntax:
```javascript
Engine.run(engine);
```
Also, we have to render everything, by using the follwing syntax:
```javascript
var Render = Matter.Render;

var render = Render.create();

Render.run(render);
```
Finally, view your code in your web browser, and you will see a circle falling down!

### Bodies other than Circles
matter.js does not only support circle bodies! You can also create the following types of bodies:
```javascript
Bodies.circle(x, y, radius) // creates a circular body
Bodies.fromVertices(x, y, vector) // creates a polygon from a bunch of vertices
Bodies.polygon(x, y, sides, radius) // creates a regular polygon from a number of sides
Bodies.rectangle(x, y, width, height) // creates a rectangular body
Bodies.trapezoid(x, y, width, height, slope) // creates a trapezoid with its base being a horizontal line
```

### Full Example
We've just got started using matter.js! Let's do a quick recap using a code example:
```javascript
// Store all the things we'll use from matter.js in some variables
var Engine = Matter.Engine,
    Render = Matter.Render,
    World = Matter.World,
    Bodies = Matter.Bodies;
    
// Create an engine
var engine = Engine.create();
var world = engine.world; // Reference the world and store it in a variable

// Create a render
var render = Render.create();

// Create some bodies
var circle = Bodies.circle(350, 160, 50); // Creates a circular body
var polygon = Bodies.polygon(400, 60, 7, 50); // Creates a regular polygon with 7 sides
var rectangle = Bodies.rectangle(450, 160, 100, 100); // Creates a rectangular body

// Add the bodies to the world
World.add(world, [circle, polygon, rectangle]);

// Run the engine
Engine.run(engine);

// Render everything
Render.run(render);
```
Just one more quick thing, notice, there's a
```javascript
World.add(world, [circle, polygon, rectangle]);
```
in this example, this array is telling you thay you can add multiple things to the world at once.
