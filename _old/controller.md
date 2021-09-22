## FPS Controller
The FPS Controller consists of two main elements, the **Camera Controller** and the **Player Controller**. 

1. The [**Camera Controller**](camera-controller.md) allows for the Player to look around and have visibility of the world, it also orients the Player Controller in the correct direction so that inputs from the keyboard are always relative to Camera direction.
2. The [**Player Controller**](player-controller.md) allows for the actual movement and interaction of the Player with the game world. The **Player Controller** functions through the use of multiple other Components.

## FPS Controller Basics
The easiest way to begin using the FPS Controller is to navigate to __Assets/Prefabs/Player__ and find ___FPSController.prefab___. Drag the prefab into the scene and it should be able to move, control the camera and interact with physics out of the box. 

It's important that you remove the existing **Main Camera** from the Scene so that you don't have 2 Cameras running at the same time.

### FPS Controller Prefab Children

To better understand what's going on, let's break the prefab into its individual GameObjects. After dragging in the prefab, look at the Hierarchy. 

![1.png]({{site.baseurl}}/1.png)

Let's break this down:

- **Controller**
	- Pivot : An Empty GameObject that is rotated by the __PlayerController__ script, it determines the direction of the Camera (this will be explained more below).
    - ForwardsDirection : An Empty GameObject that stores the forward rotation of the Player.
- **CM VCam1** : This is a __CinemachineVirtualCamera__, this allows you to add complex behaviour to the Camera with simple properties. For example, things such as Damping, Camera Offset etc. can all be modified simply in this Component. This will be covered more extensively soon.
- **Camera** : This Camera is controlled directly by the **CM VCam1**

The **FPSController** root GameObject is simply there to store the different elements, it by itself does not have any functionality.

### FPS Controller Base Properties

Some core properties of the FPSController are that the __Layer__ of the Player and all its children should always be on a separate layer called 'Player'. It should be assigned by default.

You can check it by looking in the top right corner in the Inspector window.

![2.png]({{site.baseurl}}/2.png)


### Elements of the Base Controller

Let's step one level down in the Hierarchy to the **Controller** GameObject. Focus your attention over to the Inspector window and notice all the different Components.

![REPLACE_INSPECTOR_PLAYER 20.png]({{site.baseurl}}/REPLACE_INSPECTOR_PLAYER 20.png)


So what does each one do?

1. **Transform** : Default Component that stores the __position__, __rotation__ and __scale__ values of the Player.

2. **Capsule Collider** : This Collider is mainly responsible for pushing out the Player from any walls it gets stuck in, this is not the Collider in charge of general collisions. 

[**Learn more...**](capsule-collider.md)

3. **Character Controller** : This Component is provided by default in Unity. It has some great features such as collision detection and preventing movement through objects without the need for a Rigidbody. This will work great when we need deterministic movement.

[**Learn more...**](character-controller.md)

4. **Player Input Manager** : This Component utilises the new Unity Input System to recieve events when a certain key is pressed and triggers the respective events/data changes in the FPSController.


5. **Player Input** : This Component is provided by default with the new Input System and it is in charge of determining which keys call which functions.

[**Learn more...**](player-input.md)

6. **Player Physics** : This Component has some helpful functions that can be used to determine physical properties/states of the Player such as if the Player is currently grounded.

[**Learn more...**](player-physics.md)

7. **Player Controller** : The main driver of the Player, it holds all the logic for movement. It also has some properties that determine how the Player moves in different situations.

[**Learn more...**](player-controller.md)

8. **Player Camera Controller** : This is the main driver of the Camera movement, rotation, smoothing and all its effects. It is highly configurable as it is utilising the Cinemachine system.

[**Learn more...**](camera-controller.md)

Once you are more familiar with the different Components you can start utilising them in your own modified controllers.