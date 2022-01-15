# ULTRAENGINE_RigidBodyColliders

This extension specifies collision shapes associated with a glTF node, for physics simulations and raycasting.

```json
extensions:
{
  "ULTRAENGINE_RigidBodyColliders":
  {
    "colliders":
    [
      {
        "shape": "BOX",
        "offset": [0,1,0],
        "rotation": [0,0,0],
        "size": [2,2,2]
      },
      {
        "shape": "CYLINDER"
        "size": [1,10]
      },
      {
        "shape": "SPHERE"
        "size": [2]
      },
      {
        "shape": "CONE"
        "size": [1,10]
      },
      {
        "shape": "CAPSULR"
        "size": [1,10]
      },
      {
        "shape": "MESH",
        "vertices": 4
        "faces": ???
      },      
      {
        "shape" "CONVEX_HULL"
        "vertices": 4
        "faces": ???
      }
    ]
  }
}
```
