# ノードのコネクションまとめ
```
import hou

joint1 = hou.node('obj').createNode('bone', node_name='boneA')
joint2 = hou.node('obj').createNode('bone', node_name='boneB')

joint2.setInput(0, joint1, 0)
```
ノード同士のコネクションは【setInput】関数で。  

setInput(input_index, item_to_become_input, output_index=0)

第一引数にこのノードの入力コネクタのインデックス、  
第二引数にコネクション元のノードをhou.Node型で渡す、  
第三引数にコネクション元のノードコネクタのインデックスを渡す。  

注意点は、子供にしたいノードの関数で親を引数に指定するところ。