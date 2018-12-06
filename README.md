# aframe-travel-component
A component meant to facilitate movement through a 3D environment via gaze-based input. Can be handy for cardboard movement.

By adding the travel-node to an entity, you can make the camera move to that position after it has received a 'click' event from the cursor.

![animation](http://sandbox.leunix.nl/aframe-travel-component.gif)

## API

### Component
The base name of the component is `travel-node`. In addition, there is a `travel-node-defaults` component to setup default values for all travel-node components.

### Transitions
There are three ways for the target to be transitioned from its current position to the entity's position.

### Fade
The active camera will fade out. Once it has faded out, the target will jump to this entity's position. The camera will then fade back to the scene. The *animationDur* and *animationEase* properties can be used to control the fading animation. 

This transition is on by default.

#### Jump
The target will be instantly jumped to this entity's position with no animation.

#### Move
The target will move to this entity's position. The *animationDur* and *animationEase* properties can be used to control the target's animation.

### Properties
| Property | Description | Default value |
| -------- | ----------- | ------------- |
| axis | What axises(x, y and z) will be copied when the target is moved to this position | x,z |
| animationDur | How long the animation will take during movement in miliseconds | 100 |
| animationEasing | What easing will be used during the animation | linear |
| offsetX | How far the target will be offset from this entity's x-axis | 0 |
| offsetY | How far the target will be offset from this entity's y-axis | 0 |
| offsetZ | How far the target will be offset from this entity's z-axis | 0 |
| transition | What transition will be used during movement. Available options: fade, jump or move | fade |
| travelTarget | A query selector indicating what entity will be moved | [camera] |

### travel-node-defaults
By setting the `travel-node-defaults` component on the `a-scene` element, you can setup default values that will be used on all `travel-node` elements in the scene.

## Example
```html
    <a-scene travel-node-default="axis: x,y,z; offsetY: 0.75">
        <a-sphere id="node-fade" position="2 0.25 0" radius=".25" color="#4CC3D9" travel-node></a-sphere>
        <a-sphere id="node-move" position="-2 0.25 0" radius=".25" color="#EDC34C" travel-node="transition: move"></a-sphere>
        <a-plane position="0 0 0" rotation="-90 0 0" width="5" height="5" color="#7BC8A4"></a-plane>
        <a-entity position="1 0.75 1" camera look-controls wasd-controls>
            <a-cursor></a-cursor>
        </a-entity>
    </a-scene>
```
