# wrangleで回転を扱う関数まとめ
### eulertoquaternion
vector4  eulertoquaternion(vector rotations, int order)

X,Y,Zのオイラー回転を表現したベクトルからクォータニオンを表現したvector4を作成。  
引数のorder整数値で回転順を指定。$HH/vex/include/math.hで定義された定数(例えば、XFORM_XYZ)を使用。

### quaternion
vector4  quaternion(matrix3 rotations)  
vector4  quaternion(float angle, vector axis)

指定したマトリックス、またはベクトルを軸としたクォータニオンを作成。

### qrotate
vector  qrotate(vector4 quaternion, vector v)

指定したクォータニオンで回転させたベクトルvを返す。  
つまりポイントに対して使うと変形後のポイント位置を返してくれる。

### rotate
rotate(matrix3 &m, float amount, vector axis)

指定したマトリックスに回転を適用。引数で回転量、回転軸を指定。  
例えば以下のように軸ごとに作成したマトリックスに対し回転を適用したり出来る。


```
matrix3 matX = ident();
matrix3 matY = ident();
matrix3 matZ = ident();
v@up = set(0,0,1);
vector rot = chv("rotate");

float anglex = radians(rot.x+90);
vector axisx = cross(normalize(v@up),normalize(v@N));
rotate(matX, anglex, axisx);

float angley = radians(rot.y);
vector axisy = cross(normalize(v@up),normalize(axisx));
rotate(matY, angley, axisy);

float anglez = radians(rot.z);
vector axisz = cross(normalize(axisx),normalize(axisy));
rotate(matZ, anglez, axisz);

matrix3 mat = matX * matY * matZ;

@rot= quaternion(mat);
```