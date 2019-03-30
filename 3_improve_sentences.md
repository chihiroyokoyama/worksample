selfはインスタンスオブジェクト自身を指しています。クラスの中でインスタンスオブジェクトを呼び出す際やそのインスタンスオブジェクトを呼び出す際は、selfを使用します。

selfについて説明する前に、クラスとインスタンスについて復習しましょう。クラスは、設計図のようなもの。その設計図を元につくられたモノ（オブジェクト）がインスタンスです。

では、selfの説明のために、今回は「ホテル予約システム」を作ると仮定し、コードを書いていきます。
「ホテル予約システム」には、最終的には部屋の内容（タイプと値段）を①表示する機能と、②予約を受け取る機能をつけますが、selfの説明は、①の機能をつける段階で出てきます。

各部屋のページの設計図となるclassを用意しましょう。
```rb
 class Room
 
 end
``` 
次に、各部屋がタイプ名と値段という情報が持てるように、設計図に書き加えます。
```rb
 class Room 
  attr_accesor :name
  attr_accesor :price 
 end
```
この設計図（クラス）を元に、インスタンスを生成しましょう。Room.newとすることで生成できます。生成したインスタンスは、「変数＝クラス名.new」とすることで変数に代入できます。
今回は、room1 という変数にインスタンスを代入しましょう。
```rb
 class Room 
  attr_accesor :name
  attr_accesor :price 
 end
 
room1=Room.new 
```
クラスの中では、インスタンスに情報を追加できるようにする（attr_accesor シンボルの部分）だけでなく、インスタンスに対して呼び出すメソッドを定義することもできます。
```rb
 class Room 
   attr_accesor :name
   attr_accesor :price 
   def show 
    puts "当部屋は宿泊用です（宴会不可）"　　➡️　当部屋は宿泊用です（宴会不可）　と出力されます。
   end
 end
 room1=Room.new 
 puts room1.show
```
具体的には、４０行のように、「インスタンス名.変数」とすることでクラス内で定義したメソッドを呼び出します。インスタンスに対して使うメソッドなので、インスタンスメソッドと呼びます。インスタンスメソッドは、もちろん引数(ここではdata)を受けとったり、戻り値を返したりすることも可能です。
```rb
 class Room 
   attr_accesor :name
   attr_accesor :price 
   def show(data)　 
    puts "当部屋は#{data}です"　　
   end
 end
 room1=Room.new 
 puts room1.show("宿泊用")　　　　　　　→　当部屋は宿泊用です　と出力されます。
```
さて、いよいよselfの登場です。selfは特殊な変数です。selfを使うと、クラス外にあるインスタンス変数（ここではroom1.name）を、クラス内にあるインスタントメソッド内で使うことができるようになります。さらに、selfには、呼び出し元であるインスタンス自身が代入されます。
```rb
 class Room 
   attr_accesor :name
   attr_accesor :price 
   def show_name　 
    puts "当部屋は#{self.name}です"　　
   end
 end
 room1=Room.new 
 room1.name= "シングル"　　
 room1.show_name                   →　当部屋はシングルです　と出力されます。
```

これで、「ホテル予約システム」の、①各部屋の内容を表示する機能の１つ目を作ることができました。

  


    
　　
