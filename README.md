package-loading-problem
=======================

recursive partitioning approach for the packing of different rectangles in a rectangle.

## 問題原文

> "
# 2次元パッキング問題
# 敷き詰める矩形は後述の52種のうちから選択し90度回転を認め、各一回だけ使用できる
# 解は厳密解でなくてもよいが、計算時間は一分以内を目安とせよ
#
# 問題.1 50x50 の領域になるべく隙間なく矩形を並べたとき
#        隙間の総面積を出力せよ。またそのときの並べ方を出力せよ。
#
# 問題.2 200x100 の領域になるべく隙間なく矩形を並べたとき
#        隙間の総面積を出力せよ。またそのときの並べ方を出力せよ。
#
# 名前 矩形幅 矩形高さ
a 42 18
b 35 1
c 20 25
d 29 9
e 13 15
f 6 46
g 32 28
h 12 42
i 46 43
j 28 37
k 42 5
l 3 4
m 43 33
n 22 17
o 19 46
p 48 27
q 22 39
r 20 13
s 18 50
t 36 45
u 4 12
v 23 34
w 24 15
x 42 12
y 4 19
z 48 45
A 13 8
B 38 10
C 24 42
D 30 29
E 17 36
F 41 43
G 39 7
H 41 43
I 15 49
J 47 6
K 41 30
L 21 1
M 7 2
N 44 49
O 30 24
P 35 5
Q 7 41
R 17 27
S 32 9
T 45 40
U 27 24
V 38 39
W 19 33
X 30 42
Y 34 16
Z 40 9
"

## 実行環境

Intel(R) Core(TM) i5-2520M CPU @ 2.50GHz

Linux 3.2.0-27-generic-pae #43-Ubuntu SMP Fri Jul 6 15:06:05 UTC 2012 i686 i686 i386 GNU/Linux

2.9.1.final (OpenJDK Server VM, Java 1.6.0_24).

### 答え.1

`
scala>
    import PLP._
    import PLPFrame._
    val p = Packer(boxes)
    val res = p.run(50, 50, 1000)
    val blank = res.map(x => x.area - x.filled).sum
    println(blank)
    res.map(PLPFrame(_, 5))
`

隙間の総面積は15。

![Alt blank=15 "N b J l"](Answer1.png)

### 答え.2

`
scala>
    import PLP._
    import PLPFrame._
    val p = Packer(boxes)
    val res = p.run(200, 100, 60 * 1000)
    val blank = res.map(x => x.area - x.filled).sum
    println(blank)
    res.map(PLPFrame(_, 5))
`

隙間の総面積は3338。(制限時間1分)

![Alt blank=3338 ""](Answer2.png)
