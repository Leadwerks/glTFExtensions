# ULTRA_collision_shape

## Contributors

- Josh Klint, Ultra Engine

## Status

Complete

## Dependencies

Written against the glTF 2.0 spec.

## Overview

This extension adds support for collision shapes attached to a glTF node, for physics simulations and raycasting.

## Defining Collision Shapes

Collision shapes are defined within a dictionary property in the glTF scene description file, by adding an extensions property to the top-level glTF 2.0 object and defining a ULTRA_collision_shape property with an array inside it.

Each collision shape defines a mandatory type property that designates the type of shape (box, cylinder, cone, capsule, sphere, mesh, or convex_hull). The following example defines a box with dimensions of one unit:

```json
"extensions": {
    "ULTRA_collision_shape" : {
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

Collision shapes must be attached to a node by defining the extensions.ULTRA_collision_shape property and, within that, an index into the collision shapes array using the collisionShapes property. Multiple collision shapes per node are supported, and should be treated as a single compound shape.

```json
"nodes" : [
    {
        "extensions" : {
            "ULTRA_collision_shapes" : {
                "collisionShapes" : [
                    0
                ]
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
| faces | Specifies an accessor that point to vertex data. | :white_check_mark: Yes |
| vertices | Specifies a accessor that points to face indice data. | :white_check_mark: Yes |

The vertices bufferview must specify three float values per vertex.

The faces bufferview must be made up of unsigned bytes, unsigned shorts, or unsigned integers. Each face starts with an integer indicating the number of indices in the face, followed by that number of indices. Each face can include three or more indices:

```numIndices, indices0, indice1...indiceN```
