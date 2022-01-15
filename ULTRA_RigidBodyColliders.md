# ULTRA_RigidBodyColliders

This extension specifies collision shapes associated with a glTF node, for physics simulations and raycasting.

For mesh and convex hull shapes, the vertices value is an index of a buffer view. The buffer view must specify three FLOAT values per vertex. The faces value is an index to an buffer view of integers with type INT8, INT32, or INT64. The format os the indices buffer view is as follows:

```numIndices, indices0, indice1...indiceN```

Each face starts with an integer indicating the number of indices in the face, followed by that number of indices. Each face can include three or more indices.

For cylinder and cone shapes, the Y axis is the axis around which the shape is "lathed" (technical term for this?). For cone shapes, the cone tip points in the positive direction of the Y axis.

Rotation can use four components to specicify a quaternion, or three components to specify Euler rotation.

Shape is a string value, and can be any of the following:
- BOX
- CYLINDER
- CONE
- CAPSULE
- SPHERE
- CONVEX_HULL
- MESH

Alternatively, a 4x4 matrix can be used to specify the rotation and offset. If a matrix is used, the matrix must be normalized, and the size parameter must still be included.

```json
"extensions":
{
  "ULTRA_RigidBodyColliders":
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
        "matrix": [1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1]
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
        "faces": 5
      },      
      {
        "shape" "CONVEX_HULL"
        "vertices": 4
        "faces": 5
      }
    ]
  }
}
```
