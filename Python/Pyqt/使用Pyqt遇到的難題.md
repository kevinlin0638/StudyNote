# 使用 Pyqt 遇到的難題

## 如何在視窗標題列新增時間

```
self.timer = QtCore.QTimer()
self.timer.timeout.connect(self.gettime)
self.timer.start(300)
```

新增一個 timer 在 init 裡面，然後 connect 一個 function 來更新視窗的標題!

```
    def gettime(self):
        self.date_str = strftime('%Y / %m / %d - %H:%M:%S', gmtime())
        self.setWindowTitle('Ur title ' + self.date_str)
```

$ 目前我是想到這樣做，但不確定有沒有更有效率的辦法。


## 如何將 pyqt5 裡面的 QTableView 顯示文字改成按鈕

這邊我自己上網找了滿久，找到可以使用 setIndexWidget 這個函式，去指定哪格為指定的widget，詳細用法如下

```
# 先宣告一個按鈕的物件
c = QPushButton()

# 再將指定的 (row, col) widget 改為 你宣告的 物件
self.search_table.setIndexWidget(mod.index(row, col), c)

```

如此一來就可以將顯示的東西改為按鈕了!

## QTableView 中按鈕 如何指定呼叫的函數

今天如果按鈕是固定功能的話還好做
只要

```
c.clicked.connect(Ur_Function_name)
```
將你的按鈕指定到固定的funtion就好

可是如果要 取得這個按鈕在 哪一行 哪一列 就沒辦法這樣使用，這時候有一招
使用 lambda 來建立無名函數 變數就設定為 你要的東西(Ex.目前行、列) 然後再呼叫你要的函數
實際操作如下:

```
c.clicked.connect(lambda *args, row=row, column=col: self.cellClick(row, column))
```

## QtCore.QDate 的小錯誤

在 QtCore.QDate 的物件中，有一個函式叫做.addDays(int)
養成習慣不管是print還是如何，任何加年、月、日都使用它內建的函數就好，千萬不要自己加一個int

像是如果要做 timedelta 的時候，如果 3/31 再加幾天 你用 + 1 的話 他會變 3/32 然後程式掛給你看，如果是使用.addDays(1)就會自動跳到4/1日，為避免錯誤發生，請盡量使用函數來加日。

## 獲得 timedelta 的天數、秒等等

當兩個日期物件進行加檢時，會獲得一個 timedelta 的物件，此時可以使用 內建函式 來獲得差幾天、幾秒等等
以下範例(取得差幾秒):

```
left_sec = (datetime(year=self.tomorrow.year(), month=self.tomorrow.month(), day=self.tomorrow.day(), hour=0, minute=0, second=0) - datetime.now()).total_seconds()
```

個人覺得這個拿來做跨年倒數應該不錯用 XD