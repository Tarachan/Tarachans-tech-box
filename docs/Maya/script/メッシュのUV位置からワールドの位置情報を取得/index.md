# メッシュのUV位置からワールドの位置情報を取得
```
import maya.api.OpenMaya as om2

def getPointAtUV(mesh, u, v):
    sel = om2.MSelectionList()
    sel.add(mesh)
    mesh = om2.MItMeshPolygon(sel.getDagPath(0))
    
    point = []
    space = om2.MSpace.kWorld
    for n in range(mesh.count()):
        try:
            point.append(mesh.getPointAtUV([u, v], space))
        except RuntimeError:
            pass
        mesh.next(n)
    
    return point

# example
print getPointAtUV('pPlane1', 0.45, 0.45)
```
***
`getPointAtUV(uvPoint, space=kObject, uvSet=None, tolerance=0) -> MPoint`  

`* uvPoint ([float, float]) - The UV value to try to locate`  
`* space (int) - The coordinate system for this operation`  
`* uvSet (string) - UV set to work with`  
`* tolerance (float) - tolerance value to compare float data type`  
***

`MItMeshPolygon`クラス内にある`getPointAtUV()`関数でuv値を指定すれば、指定したuvのポイントがシーンのどの位置にあるかを返してくれます。  
まずMIt～のクラスはイテレーターという連続処理に特化したクラスで、`MItMeshPolygon`の場合ポリゴンの処理に特化したクラスです。  
使い方は`count()`関数でメッシュの全ポリゴンの数を取得後、forループ内で`next()`関数を実行すると順番にすべてのフェースにアクセスできます。  
指定したuv値がフェース上にない場合RuntimeErrorを返すので、上記スクリプトでは無視する処理を入れています。

[MItMeshPolygon help(Maya2017)](http://help.autodesk.com/view/MAYAUL/2017/JPN/?guid=__py_ref_class_open_maya_1_1_m_it_mesh_polygon_html)