# 選択したメッシュの各情報を取得
```
 import maya.api.OpenMaya as om
 
 sel = om.MGlobal.getActiveSelectionList()
 dag = sel.getDagPath(0)
 meshFn = om.MFnMesh(dag)
 
 u'''
 全頂点の位置
 Return:
     MPointArray
 '''
 print meshFn.getPoints()
```

apiを使用すればメッシュの各情報に簡単にアクセス可能。
MFnMeshの引数には取得したオブジェクトのMDagPathを指定してあげる必要がある。

例えば`getPoints()`関数ですべての頂点の位置情報を取得できる。

[MFnMesh help(Maya2017)](http://help.autodesk.com/view/MAYAUL/2017/JPN/?guid=__py_ref_class_open_maya_1_1_m_fn_mesh_html)
 