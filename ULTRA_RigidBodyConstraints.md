# ULTRA_RigidBodyConstraints

```json
"extensions":
{
  "ULTRA_RigidBodyConstraints":
  {
    "joints":
    [
      {
        "parent": 1,
        "child": 2,
        "type": "HINGE",
        "limits": [-45,45]
      },
      {
        "parent": 2,
        "child": 3,
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
