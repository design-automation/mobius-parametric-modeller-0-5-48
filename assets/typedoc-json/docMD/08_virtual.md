# VIRTUAL    

## Ray  
* **Description:** Creates a ray, centered at the origin.
A ray is defined by a list of two lists, as follows: [origin, direction_vector].  
* **Parameters:**  
  * *origin:* Origin of ray: Position, Vertex, Point, or a list of three numbers  
  * *dir_vec:* Direction of Ray: Vector, or list of three numbers  
* **Returns:** A list consisting of an origin and a vector, [origin, vector].  
* **Examples:**  
  * virtual.Ray([1,2,3],[4,3,2])  
    Creates a ray from [1,2,3] with the vector [4,3,2].

  
  
## Plane  
* **Description:** Creates a plane.
A plane is define by a list of three lists, as folows: [origin, x_vector, xy_vector].  
* **Parameters:**  
  * *origin:* Origin of plane: Position, Vertex, Point, or a list of three numbers  
  * *x_vec:* X axis vector of the plane: List of three numbers  
  * *xy_vec:* A vector in the xy plane (not parallel to the x axis vector): List of three numbers  
* **Returns:** A list consisting of an origin and two normalised perpendicular vectors.  
* **Examples:**  
  * virtual.Plane ([1,2,3],[4,3,2],[1,1,1])  
    Creates a plane with its origin positioned at [1,2,3] and two normalised perpendicular vectors
[0.74..., 0.56..., 0.37...] and [-0.53..., 0.15..., 0.83...] representing the X and Y axes of the plane.
  
  
## RayFromPlane  
* **Description:** Create a ray, from a plane.
The direction will be along the z axis.
A plane is define by a list of three lists, as folows: [origin, x_vector, y_vector].
A ray is defined by a list of two lists, as follows: [origin, direction_vector].  
* **Parameters:**  
  * *planes:* undefined  
* **Returns:** Ray or list of rays.  
  
## GetRay  
* **Description:** Returns a ray for an edge, a face, or a polygons. For edges, it returns a ray along the edge, from teh start vertex to the end vertex
For a face or polygon, it returns the ray that is the z-axis of the plane.
~
For an edge, the ray vector is not normalised. For a face or polygon, the ray vector is normalised.  
* **Parameters:**  
  * *entities:* An edge, a face, or a polygon, or a list.  
* **Returns:** The ray.  
  
## GetPlane  
* **Description:** Returns a plane from a polygon, a face, a polyline, or a wire.
For polylines or wires, there must be at least three non-colinear vertices.
~
The winding order is counter-clockwise.
This means that if the vertices are ordered counter-clockwise relative to your point of view,
then the z axis of the plane will be pointing towards you.  
* **Parameters:**  
  * *entities:* Any entities  
* **Returns:** The plane.  
  
## GetBBox  
* **Description:** Returns the bounding box of the entities.
The bounding box is an imaginary box that completley contains all the geometry.
The box is always aligned with the global x, y, and z axes.
The bounding box consists of a list of lists, as follows [[x, y, z], [x, y, z], [x, y, z], [x, y, z]].
- The first [x, y, z] is the coordinates of the centre of the bounding box.
- The second [x, y, z] is the corner of the bounding box with the lowest x, y, z values.
- The third [x, y, z] is the corner of the bounding box with the highest x, y, z values.
- The fourth [x, y, z] is the dimensions of the bounding box.
~  
* **Parameters:**  
  * *entities:* The etities for which to calculate the bounding box.  
* **Returns:** The bounding box consisting of a list of four lists.  
  
## Distance  
* **Description:** Calculates the distance between a ray or plane and a list of positions.
~  
* **Parameters:**  
  * *ray_or_plane:* Ray or a plane.  
  * *entities:* A position or list of positions.  
  * *method:* Enum; all_distances or min_distance.  
* **Returns:** Distance, or list of distances.  
* **Examples:**  
  * distance1 = virtual.Distance(ray, positions, all_distances)  
    Returns a list of distances between the ray and each position.
  
  
## Intersect  
* **Description:** Calculates the xyz intersection between a ray or a plane and a list of entities.
~
For a ray, the intersection between the ray and one or more faces is return.
The intersection between each face triangle and the ray is caclulated.
This ignores the intersections between rays and edges (including polyline edges).
~
For a plane, the intersection between the plane and one or more edges is returned.
This ignores the intersections between planes and face triangles (including polygon faces).
~  
* **Parameters:**  
  * *ray_or_plane:* Either a ray or a plane.  
  * *entities:* List of entities.  
* **Returns:** A list of xyz intersection coordinates.  
* **Examples:**  
  * coords = virtual.Intersect(plane, polyline1)  
    Returns a list of coordinates where the plane intersects with polyline1.
  
  
## VisRay  
* **Description:** Visualises a ray by creating a line.  
* **Parameters:**  
  * *rays:* A list of two list of three coordinates [origin, vector]: [[x,y,z],[x',y',z']]  
  * *scale:* undefined  
* **Returns:** entities, a line representing the ray.  
* **Examples:**  
  * ray1 = virtual.visRay([[1,2,3],[0,0,1]])
  
  
## VisPlane  
* **Description:** Visualises a plane by creating a polygon and axis lines.  
* **Parameters:**  
  * *planes:* undefined  
  * *scale:* undefined  
* **Returns:** Entities, a polygon and two polyline representing the plane.  
* **Examples:**  
  * plane1 = virtual.visPlane(position1, vector1, [0,1,0])  
    Creates a plane with position1 on it and normal = cross product of vector1 with y-axis.
  
  
## VisBBox  
* **Description:** Visualises a bounding box by adding geometry to the model.  
* **Parameters:**  
  * *bboxes:* A list of lists.  
* **Returns:** Entities, twelve polylines representing the box.  
* **Examples:**  
  * bbox1 = virtual.viBBox(position1, vector1, [0,1,0])  
    Creates a plane with position1 on it and normal = cross product of vector1 with y-axis.
  
  
