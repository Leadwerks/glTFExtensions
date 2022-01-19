# ULTRA_CollisionShape

## Contributors

- Josh Klint, Ultra Engine

## Status

Complete

## Dependencies

Written against the glTF 2.0 spec.

## Overview

This extension adds support for collision shapes attached to a glTF node, for physics simulations and raycasting.

## Defining Collision Shapes

Collision shapes are defined within a dictionary property in the glTF scene description file, by adding an extensions property to the top-level glTF 2.0 object and defining a ULTRA_CollisionShape property with an array inside it.

Each collision shape defines a mandatory type property that designates the type of shape (box, cylinder, cone, capsule, sphere, mesh, or convex_hull). The following example defines a box with dimensions of one unit:

```json
"extensions": {
    "ULTRA_CollisionShape" : {
        "coliisionShapes": [
            {
                "size": [
                    1.0,
                    1.0,
                    1.0
                ],
                "type": "box"
            }
        ]
    }
}
```

## Adding Collision Shape Instances to Nodes

Collision shapes must be attached to a node by defining the extensions.ULTRA_CollisionShape property and, within that, an index into the collision shapes array using the collisionShape property.

```json
"nodes" : [
    {
        "extensions" : {
            "ULTRA_CollisionShape" : {
                "collisionShape" : 0
            }
        }
    }            
]
```

The collision shape will inherit the transform of the node, including scale. Scale may be non-uniform. If the position or rotation properties are present in the collision shape definition, those will be used to further orient the shape in node space.

## Collision Shape Properties

| Property | Description | Required |
|---|---|---|
| position | Specifies the offset of the shape when attached to a node | No |
| rotation | Euler or quaternion rotational offset | No |
| size | Specifies the width, height, and depth. | :white_check_mark: Yes |
| type | Declares the type of the collision shape. | :white_check_mark: Yes |

## Collision Shape Types

The following collision shapes are supported:

- box
- cylinder
- cone
- capsule
- sphere
- convex_hull
- mesh

For cylinder, cone, and capsule shapes, the Y axis is the axis of the shape, with the cone tip pointing in the positive direction.

## Mesh and Convex Hull Definitions

Mesh and convex hull shape definitions use two additional properties:

| Property | Description | Required |
|---|---|---|
| faces | Specifies a bufferview where face indices are stored. | :white_check_mark: Yes |
| vertices | Specifies a bufferview where vertices are stored. | :white_check_mark: Yes |

The vertices bufferview must specify three FLOAT values per vertex.

The faces bufferview must be made up of integers with type INT8, INT32, or INT64. Each face starts with an integer indicating the number of indices in the face, followed by that number of indices. Each face can include three or more indices:

```numIndices, indices0, indice1...indiceN```
