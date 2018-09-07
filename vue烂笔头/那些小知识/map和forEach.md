###  用法上区别
1. forEach
    - forEach()不会返回有意义的值的。我们在回调函数中直接修改arr的值。
    
        ```
        let arr = [1,2,3,4]; 
        arr.forEach(function (e,i) {
          arr[i] = e*2;
        })
        console.log(arr); // [2,4,6,8]
        ```

2. map
    - map()会返回一个全新的数组，原本的数组不受到影响
    
        ```
        let arr2 = [1, 2, 3, 4];
        let newArr = arr2.map(function (e) {
            return e*2
        })
        console.log(newArr); // [2,4,6,8]
        console.log(arr2); // [1,2,3,4]
        ```

### 适用环境
1. forEach适合于你并不打算改变数据的时候，而只是想用数据做一些事情 – 比如存入数据库或则打印出来。
    
    ```
    let arr3 = ['a', 'b', 'c', 'd'];
    arr3.forEach((letter) => {
      console.log(letter); 
    });
    ```

2. map()适用于你要改变数据值的时候。不仅仅在于它更快，而且返回一个新的数组。这样的优点在于你可以使用复合(composition)(map(), filter(), reduce()等组合使用)来玩出更多的花样。
    
    ```
    // 先使用map将每一个元素乘以2，然后紧接着筛选出那些大于5的元素。最终结果赋值给arr2
    
    let arr = [1, 2, 3, 4, 5];
    let arr2 = arr.map(num => num * 2).filter(num => num > 5);
    
    // arr2 = [6, 8, 10]
    ```

### 速度
1. map 比 forEach更快

### 总结
1. 能用forEach()做到的，map()同样可以。反过来也是如此。
2. map()会分配内存空间存储新数组并返回，forEach()不会返回数据。
3. forEach()允许callback更改原始数组的元素。map()返回新的数组。


