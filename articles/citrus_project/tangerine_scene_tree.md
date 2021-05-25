# Tangerine scene tree

## What is a scene tree and why do we need one?

A scene tree is an object tree of class SceneItem, which is a hierarchy parallel to the node tree. But unlike the node hierarchy, it takes into account the placement of nodes within folders, the hierarchical organization of bones, etc. This significantly simplifies visualization of the scene structure, as well as its editing, hiding the whole mechanism of index recalculation for folders and bones behind the scene tree API. Visually, the scene tree can be seen as a timeline element, on the animations panel and on the scene hierarchy panel.
The reference to the root of the tree is in the document: Document.Current.SceneTree. The node of the tree is an object of the SceneItem class (currently Row, will be renamed to SceneItem in the future).

## How to modify the scene tree

1. In order to properly add nodes, folders, animations, etc., you must use the `LinkSceneItem.Perform()` method.
You can never add nodes directly to a NodeList collection. This is because within itself a node has an additional folder hierarchy that is not directly created to the NodeList. And if you add a node to the NodeList through `AddIntoCollection.Perform()` the folder structure will be broken.

2. To build a scene tree for a new node (just created or cloned) just execute the following code:
 `var sceneItem = Document.Current.SceneTreeBuilder.BuildForNode(node)`. 
 Then you can add it to the document's scene tree like this: `LinkSceneItem.Perform(Document.Current.SceneItem, 0, sceneItem)`;
 But as said in the previous paragraph, there is an overload `LinkSceneItem.Perform()` which takes a Node and internally calls `BuildForNode()`.

3. To translate a node, animation, property into an existing SceneItem you need to use the `Document.Current.GetSceneItemForObject()` method.

4. Bones are also added to nodes and parent bones via `LinkSceneItem.Perform()`. If the parent SceneItem is also a bone, the index passed to this method is the index of the binding of the bone to the parent bone.

5. If the current SceneItem refers to a node, its children (the SceneItem.Items collection) are arranged in the following order: animations, animated properties, child nodes. Accordingly, if the parent node has 1 animation and 2 animated properties, then calling
 `LinkSceneItem.Perform(parentNodeItem, 0, childNodeItem);` 
 will insert the childNodeItem not at the zero position, but at the third position in the parentNodeItem.Items list.