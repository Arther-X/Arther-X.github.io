---
layout: post
title: Go for Javaers -- Slice
category: 读书
keywords: 阅读,书单
---

给Java程序猿的Go语言入门 -- Slice 切片

s1 := []int{1,2,3} // []中没有写数字
fmt.Println(s1, len(s1), cap(s1))

s2 := []int{0, 1, 2, 5: 100}
fmt.Println(s2, len(s2), cap(s2))

cap
s3 := make([]int, 3)
s4 := make([]int, 3, 6)



从数组中截取slice
data := [...]int{0, 1, 2, 3, 4, 5, 6}
slice := data[1:4:5]  //[low:high:max]

            +- low  high -+     +- max              len = high - low
            |             |     |                   cap = max - low 
      +---+---+---+---+---+---+---+            +---------+---------+---------+
data  | 0 | 1 | 2 | 3 | 4 | 5 | 6 |      slice | pointer | len = 3 | cap = 4 |
      +---+---+---+---+---+---+---+            +---------+---------+---------+
          |<-- len -->|   |                         |
          |<---- cap ---->|                         |
          +----<<<---- slice.array pointer ----<<<--|



re-slice
基于已有的slice创建新的slice对象，以便在cap允许范围内调整属性
s := []int {0, 1, 2, 3, 4, 5, 6, 7, 8, 9}
s1 := s[2:5]        // [2,3,4]
s2 := s1[2:6:7]     // [4,5,6,7]
s3 := s2[3:6]       // Error 10

      +---+---+---+---+---+---+---+---+---+---+
data  | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 |
      +---+---+---+---+---+---+---+---+---+---+
      0       2           5
              +---+---+---+---+---+---+---+---+
 s1           | 2 | 3 | 4 |   |   |   |   |   |     len = 3, cap = 8
              +---+---+---+---+---+---+---+---+
              0       2               6   7
                      +---+---+---+---+---+
 s2                   | 4 | 5 | 6 | 7 |   |         len = 4, cap = 5
                      +---+---+---+---+---+
                      0           3   4   5
                                  +---+---+---+
 s3                               | 7 | 8 | x |     error: slice bounds out of range
                                  +---+---+---+

slice使用
slice := []int{1, 2, 3, 4, 5}
fmt.Println(slice[4])   // 5
slice[0] = 100
fmt.Println(slice)      // [100,2,3,4,5]

追加
newSlice := append(slice, 6, 7, 8)
fmt.Println(newSlice)


copy
data := [...]int{0, 1, 2, 3, 4, 5, 6, 7, 8, 9}
s := data[8:]     // [8,9]
s2 := data[:5]    // [8,9,2,3,4]
copy(s2, s)       // [8,9,2,3,4,5,6,7,8,9]

扩容
s := make([]int, 0, 1)
c := cap(s)
for i := 0; i < 50; i++ {
	s = append(s, i)
	if n := cap(s); n > c {
		fmt.Printf("cap: %d -> %d \n", c, n)  // 2倍速扩容
		c = n
	}
}


