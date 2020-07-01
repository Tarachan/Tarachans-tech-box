# VEXの基礎
## 変数
主にwrangleでの変数の型宣言方法。
### データタイプ
#### int
```
int count = 1;
```
#### float
```
float weight = 1.5;
```
#### string
```
string str = "A massage";
```
#### array
```
int myArray[] = {1,2,3,4,5};
```
#### vector
```
vector position = {1,2,3};
```
#### matrix
```
matrix myMatrix = { {1,1,1,1}, {2,2,2,2}, {3,3,3,3}, {4,4,4,4} };
```

### オペレーション
```
int count = 1;
// 変数に値を足す方法。これらは同じ結果。
count = count + 1;
count += 1;
count ++;
```

### 比較演算 論理演算
```
int count = 1;
int result = 0;
// 同じ場合
if(count == 0){
    result = count;
}
// 違う場合
if(count != 0){
    result = count;
}
// ～かつ、～の場合
if(count != 0 && count <= 1{
    result = count;
}
// ～または、～の場合
if(count != 0 || count <= 1{
    result = count;
}
```