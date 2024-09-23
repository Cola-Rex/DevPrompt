# Sample Prompts and Outputs

本文件提供了一些示例 Prompt 及其对应的输入和输出，帮助您了解如何使用本项目的 Prompt 集合。

## 示例目录

- [示例 1：Python 函数生成](#示例-1python-函数生成)
- [示例 2：Java 类与对象](#示例-2java-类与对象)
- [示例 3：Go 并发编程](#示例-3go-并发编程)
- [示例 4：C++ 内存管理](#示例-4c-内存管理)

---

### 示例 1：Python 函数生成

**Prompt：**

```
请帮我编写一个函数，输入一个整数列表，返回其中所有偶数的平方组成的新列表。
```

**输入：**

```python
input_list = [1, 2, 3, 4, 5, 6]
```

**生成的代码：**

```python
def get_even_squares(numbers):
    return [x**2 for x in numbers if x % 2 == 0]

# 测试函数
input_list = [1, 2, 3, 4, 5, 6]
result = get_even_squares(input_list)
print(result)  # 输出: [4, 16, 36]
```

**输出：**

```
[4, 16, 36]
```

---

### 示例 2：Java 类与对象

**Prompt：**

```
请编写一个名为 `Employee` 的类，包含姓名、职位和薪水属性，并实现一个方法用于显示员工的完整信息。
```

**生成的代码：**

```java
public class Employee {
    private String name;
    private String position;
    private double salary;

    // 构造函数
    public Employee(String name, String position, double salary) {
        this.name = name;
        this.position = position;
        this.salary = salary;
    }

    // 显示员工信息的方法
    public void displayInfo() {
        System.out.println("姓名: " + name);
        System.out.println("职位: " + position);
        System.out.println("薪水: $" + salary);
    }

    // 主函数进行测试
    public static void main(String[] args) {
        Employee emp = new Employee("张三", "软件工程师", 8000.0);
        emp.displayInfo();
    }
}
```

**输出：**

```
姓名: 张三
职位: 软件工程师
薪水: $8000.0
```

---

### 示例 3：Go 并发编程

**Prompt：**

```
如何使用 Goroutine 实现并发操作？请提供一个示例，计算多个数字的平方并输出结果。
```

**生成的代码：**

```go
package main

import (
    "fmt"
    "sync"
)

func square(num int, wg *sync.WaitGroup) {
    defer wg.Done()
    fmt.Printf("%d 的平方是 %d\n", num, num*num)
}

func main() {
    numbers := []int{1, 2, 3, 4, 5}
    var wg sync.WaitGroup

    for _, num := range numbers {
        wg.Add(1)
        go square(num, &wg)
    }

    wg.Wait()
    fmt.Println("所有计算完成")
}
```

**输出（可能顺序不同）：**

```
1 的平方是 1
2 的平方是 4
3 的平方是 9
4 的平方是 16
5 的平方是 25
所有计算完成
```

---

### 示例 4：C++ 内存管理

**Prompt：**

```
请示范如何使用智能指针 `std::shared_ptr` 和 `std::unique_ptr` 来管理动态内存。
```

**生成的代码：**

```cpp
#include <iostream>
#include <memory>

void sharedPointerExample() {
    std::shared_ptr<int> ptr1 = std::make_shared<int>(10);
    {
        std::shared_ptr<int> ptr2 = ptr1;
        std::cout << "共享智能指针，引用计数: " << ptr1.use_count() << std::endl;
    }
    std::cout << "退出内部作用域，引用计数: " << ptr1.use_count() << std::endl;
}

void uniquePointerExample() {
    std::unique_ptr<int> ptr = std::make_unique<int>(20);
    std::cout << "唯一智能指针的值: " << *ptr << std::endl;
    // std::unique_ptr<int> ptr2 = ptr; // 这行会编译错误，unique_ptr 不可复制
}

int main() {
    sharedPointerExample();
    uniquePointerExample();
    return 0;
}
```

**输出：**

```
共享智能指针，引用计数: 2
退出内部作用域，引用计数: 1
唯一智能指针的值: 20
```

---

**备注：**

