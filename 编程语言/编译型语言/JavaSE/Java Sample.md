## 0x01_冒泡排序

-----

```java

public class Test {

    public static void main(String[] args) {

        int[] array = {155, 122, 15, 8, 56, 74, 136, 987, 87, 89, 58};

        int n = array.length;

        for (int i = 0; i < n - 1; i++) {

            for (int j = 0; j < n - i - 1; j++) {

                if (array[j] > array[j + 1]) {

                    int temp = array[j];

                    array[j] = array[j + 1];

                    array[j + 1] = temp;

                }

            }

        }

        System.out.println("排序后的数据: ");

        for (int num : array) {

            System.out.print(num + " ");

        }

    }

}

```

<br/>

  

### 程序运行

-----

```java

排序后的数据:

8 15 56 58 74 87 89 122 136 155 987

```

<br/>

  

## 0x02_1~100累加和

-----

```java

public class Test {

    public static void main(String[] args) {

        int sum = 0;

        int number = 1;

  

        while (number <= 100) {

            sum += number;

            number++;

        }

        System.out.println("1到100的累加和: " + sum);

    }

}

```

### 程序运行

-----

```java

1到100的累加和: 5050

```

## 0x03_输入5个学生的成绩并计算平均分，输出平均分和最高分

-----

```java

import java.util.Scanner;

  

public class Test {

    public static void main(String[] args) {

        Scanner scanner = new Scanner(System.in);

        double sum = 0;

        double max = Double.MIN_VALUE;

  

        System.out.println("请输入5个学生的成绩：");

        for (int i = 0; i < 5; i++) {

            double score = scanner.nextDouble();

            sum += score;

            if (score > max) {

                max = score;

            }

        }

        double average = sum / 5;

        System.out.println("平均分: " + average);

        System.out.println("最高分: " + max);

    }

}

```

### 程序运行

-----

```java

请输入5个学生的成绩：

12

23

345

56

34

平均分: 94.0

最高分: 345.0

  

```

## 0x04_用接口定义图形类，求圆和长方形的面积

-----

```java

interface Shape {

    double getArea();

}

  

class Circle implements Shape {

    private double radius;

  

    public Circle(double radius) {

        this.radius = radius;

    }

  

    @Override

    public double getArea() {

        return Math.PI * radius * radius;

    }

}

  

class Rectangle implements Shape {

    private double length;

    private double width;

  

    public Rectangle(double length, double width) {

        this.length = length;

        this.width = width;

    }

  

    @Override

    public double getArea() {

        return length * width;

    }

}

  

public class Test {

    public static void main(String[] args) {

        Circle circle = new Circle(5.0);

        double circleArea = circle.getArea();

        System.out.println("圆的面积为：" + circleArea);

  

        Rectangle rectangle = new Rectangle(4.0, 6.0);

        double rectangleArea = rectangle.getArea();

        System.out.println("长方形的面积为：" + rectangleArea);

    }

}

```

### 程序运行

-----

```java

  

```

## 0x02_1~100累加和

-----

```java

  

```

### 程序运行

-----

```java

  

```