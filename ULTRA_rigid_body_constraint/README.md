# ULTRA_rigid_body_constraint

This extension adds constraints to glTF nodes, for "ragdoll" effects or other physics simulations.

If the position value is not specified, the constraint will be positioned at the child node's position in world space.


```json
"extensions":
{
  "ULTRA_RigidBodyConstraints":
  {
    "constraints":
    [
      {
        "parent": 1,
        "child": 2,
        "position" [0,0,0],
        "type": "HINGE",
        "limits": [-45,45]
      },
      {
        "parent": 2,
        "child": 3,
        "position" [0,0,0],
        "type": "PISTON",
        "limits": [-1,1]
      },
      {
        "parent": 2,
        "child": 3,
        "type": "BALL_AND_SOCKET",
        "limits": [45,null]
      },
      {
        "parent": 2,
        "child": 3,
        "type": "FIXED"
      }       
    ]
  }
}
```
