# 基本

## 出力

print は `puts`
コメントアウトは`#`

変数に記号は不要。

```ruby
name = 'taro'

puts name
```

変数展開は、
`puts "名前は、#{name}です"`

## if文

```ruby
score = 92

if score > 80
  puts 'よくできました'
end
```

## 比較は ==

```ruby

score = 100

if score == 100
  puts "よくできました"

# rubyは、elsif
elsif score > 60
  puts "まずまずです"
else
  puts "がんばりましょう"
end

```

## 配列

配列は、phpと同じ

```ruby
languages = ['日本語', '英語', 'スペイン語']
puts languages
```

## foreach

基本形は、

```ruby
arrays.each do | array |
    # 処理
end
```

例

```ruby
languages = ["日本語", "英語", "スペイン語"]

languages.each do |language|
  puts "#{language}を話せます"
end

```

## 連想配列 = ハッシュ

phpの連想配列は、rubyだとハッシュという。

```ruby
exam = {"subject" => "Math", "score" => 80}

# キー「"subject"」の値を「"Science"」に更新してください
exam['subject'] = 'Science'

# キーが「"grade"」、値が「"good"」の要素を追加してください
exam['grade'] = 'good'

# キー「"grade"」の値を出力してください
puts exam['grade']
```

## シンボル

文字列とは別にシンボルがある。
`puts "ruby"` === `puts :ruby`

シンボルは、ハッシュのキーとしてよく使われます。
ハッシュのキーの部分を「:name」という様に、シンボルを用いた場合には、
その値を用いる時も「user[:name]」とシンボルで指定する必要があります。

```ruby
# キーをシンボルで書き換えてください
exam = {:subject => "Math", :score => 80}

# キー「:score」の値を出力してください
puts exam[:score]
```

更に、配列内でのシンボル利用は以下のように省略できる。

```ruby
# {シンボル: value}
exam = {subject: "Math", score: 80}

puts "#{exam[:subject]}: #{exam[:score]}点"

exam = {subject: "Math"}
if exam[:score]
  puts "#{exam[:subject]}の結果は#{exam[:score]}点です"
else
  puts "#{exam[:subject]}の結果は分かりません"
end

```

### シンボル２

要素がシンボルの配列も作成することができる。

```ruby
# 要素がハッシュの配列を作成してください
exams =[
  {subject: "Math", score: 80},
  {subject: "Science", score: 55}
]

# インデックス番号が1の要素の値を出力してください
puts exams[1]
puts exams[1][:score]

```

### function

基本形は、

```ruby
def fc
#   処理
end

# 実行
fc
```

例

```ruby
def introduce
  puts "こんにちは"
  puts "私はにんじゃわんこです"
  # 出力を追加してください
  
end

puts "-----自己紹介-----"
# introduceメソッドを呼び出してください
introduce

#引数あり
def print_info(item)
  puts "わんこでんきへようこそ！"
  puts "今日は#{item}がセール中です！"
end

print_info("ヘッドホン")


# reutrn
def discount(price)
# 「price / 2」を戻り値として返してください
 return price / 2
end
puts "テレビがセール中です！"

half_price = discount(15000)
puts "特別価格で#{half_price}円です"
```

### 特別な関数 boolean

boolianを返す変数は`?`をつける。
呼び出すときも`?`つける

```ruby
# shipping_free?メソッドを定義してください
def shipping_free?(price)
  return price >= 5000
end

# if文の条件式でshipping_free?メソッドを呼び出してください
if shipping_free?(3000)
 puts "5000円以上のお買い上げなので送料はいただきません"
else
 puts "追加で送料をいただきます"
end

```

### 特別な関数 キーワード引数

引数にシンボルを用いると、引数の順番を変えても問題なくなる。

```ruby
# キーワード引数を使うように書き換えてください
def buy(item:, price:, count:)
 puts "#{item}を#{count}台のお買い上げです"
 puts "合計金額は#{price * count}円です"
end

# キーワード引数を使うように書き換えてください
buy(item: "テレビ", price: 15000, count: 2)

```

### クラス

クラスは、
クラスの作成→インスタンスの利用、という流れになる。

- 定義
  - class名の頭文字は大文字
  - 最後は`end`でしめる。

```ruby

class Menu
  # インスタンス変数
  attr_accessor :name
  attr_accessor :price

    def info
    # インスタンス変数は、self.var
    return "#{self.name} #{self.price}円"
  end
end

# Menuクラスのインスタンスを生成
menu1 = Menu.new

# menu1のprice, nameに代入
menu1.name = "ピザ"
menu1.price = 800

# menu1のpriceを出力
puts menu1.price

# info関数を呼び出す
puts menu1.info
```

### クラス 2

phpのconstructorは`initialize`を利用する。

```ruby
class Menu
  attr_accessor :name
  attr_accessor :price
  
  def initialize(name:, price:)
    self.name = name
    self.price = price
  end
  
  def info
    return "#{self.name} #{self.price}円"
  end
  
  def get_total_price(count)
    total_price = self.price * count
    if count >= 3
      total_price -= 100
    end
    return total_price
  end
end

# 引数を渡してインスタンスを生成してください
menu1 = Menu.new(name: 'すし', price: 1000)
puts menu1.info
```

### クラス 3

- phpの`require`は、rubyの`require`
- ↑で定義したクラスのインスタンスを作り、配列に入れる。

```ruby
menu1 = Menu.new(name: "ピザ", price: 800)
menu2 = Menu.new(name: "すし", price: 1000)
menu3 = Menu.new(name: "コーラ", price: 300)
menu4 = Menu.new(name: "お茶", price: 200)

# 変数menusを定義して配列を代入してください
menus = [menu1, menu2, menu3, menu4]

# 変数indexを定義して「0」を代入してください

# phpのforeachみたいにkeyはないから、外から呼ぶ。
index = 0
menus.each do |menu|
  # 番号をつけてメニューの内容が出力されるように書き換えてください
  puts "#{index}. " + menu.info
  
  # 変数indexに1を加えて値を更新してください
  index += 1
end
```
