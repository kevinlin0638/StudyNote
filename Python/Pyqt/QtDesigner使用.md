# Qt Designer 使用

## 注意布局

為了適應不同的視窗大小，使用布局(Layout)變成一件非常重要的事情，它可以讓元件們依照視窗大小的改變來改變相對位置，由於筆者一開始在使用時沒有注意布局的使用，導致元件皆屬於絕對位置，彈性大幅縮小，因為把視窗大小固定，才解決了元件消失的問題。

## Label的使用

右鍵變更純文字的話無法指定字體、大小與顏色，可以使用右鍵 變更 Rich Text 來快速地變更字體、大小與顏色。

## QLineEdit的使用

可以在屬性樹裡面找到 Echomode 來更改文字顯示模式，使用 Password 來遮蔽密碼。

## QListView vs QListWidget

QListView 為較為底層的東西，可以自己指定 Model ，使用時較為麻煩，但是彈性較高，相對之下 QListWidget 是繼承 QListView 的類別，可以直接使用內建函式去新增 Item 不須自行指定 Model 













































# Reference
1. https://tnlin.wordpress.com/2017/03/05/%E7%AC%AC%E4%B8%80%E6%AC%A1%E5%AF%ABpyqt5%E5%B0%B1%E4%B8%8A%E6%89%8B/