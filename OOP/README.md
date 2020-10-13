# 10 / 13



### 1. OOP(객체지향프로그로밍)

#### 1. 개요

> 프로그래밍 패러다임 중 하나로, 필요한 데이터를 추상화 시켜서 상태와 행위를 가진 객체를 만들고, 그 객체를 유기적인 상호작용을 통해 로직을 구성하는 프로그래밍 방법입니다.



#### 2. 장점

- 코드의 재사용성이 높다.
- 대규모 프로젝트에 적합하다.
- 자연적인 모델링 덕분에 이해 및 설계가 용이하다.
- 개발 및 유지보수가 용이하다.



#### 3. 특징

1. 캡슐화
   - 데이터와 함수를 묶는 것을 의미함
   - 캡슐화를 통하여 정보은폐가 되어, 오류의 파급력이 적어진다.
   - 캡슐화된 객체들은 재사용이 용이핟,
2. 추상화
   - 객체의 속성중 중요하고 공통적인 것들을 모아 개략화, 모델링 하는것
3. 상속
   - 상위 클래스의 상태 및 기능을 하위 클래스가 모두 물려 받는 것
4. 다형성
   - 하나의 메시지에 대해 각 객체가 가지고 있는 고유한 방법으로 응답할 수 있는 능력
   - 오버라이딩으로 구현이 가능하다.



#### 4. 설계원칙 (SOLID)

1. 단일 책임 원칙

   > 하나의 클래스는 하나의 책임을 가져야 한다.

2. 개방-폐쇄 원칙

   > 확장에는 열려있어야 하고 변경에는 닫혀있어야 한다.

3. 리스코프 치환 원칙

   > 상위 타입의 객체를 하위 타입의 객체로 치환해도 상위 타입을 사용하는 프로그램은 정상적으로 작동하여야 한다.

4. 인터페이스 분리 원칙

   > 인터페이스는 그 인터페이스를 사용하는 클라이언트를 기준으로 나뉘어져야한다.

5. 의존 역전 원칙

   > 고수준의 모듈은 저수준의 모듈 구현에 의존해서는 안된다. 즉, 변하기 어려운 추상 클래스, 인터페이스에 의존하여야 한다.



#### 5. 오버라이딩, 오버로딩

1. 오버라이딩 : 상위 클래스가 가지고 있는 메서드를 하위 메서드에서 재정의 해서 사용하는 것

   ```c#
   class Cat
   {
       public virtual void sound()
       {
           Console.WriteLine("Meow Meow");
       }
       
   }
   class Tiger : Cat
   {
       public override void sound()
       {
           Console.WriteLine("Roar Roar");
       }
   }
   class Program
   {
       static void Main(string[] args)
       {
           Cat cat = new Cat();
           Tiger tiger = new tiger();
           cat.sound();
           // "Meow Meow"
           tiger.sound();
           // "Roar Roar"
           ((Cat)tiger).sound();
           // "Roar Roar"
       }
   }
   ```



2. 오버로딩: 메서드의 이름은 동일하지만 매개변수의 유형을 다르게 하여 사용

   ```c#
   class OverloadTest
   {
       public static void Method(int val)
       {
           Console.WriteLine("int");
       }
       public static void Method(string val)
       {
           Console.WriteLine("string!!");
       }
   }
   class Program
   {
       static void Main(string[] args)
       {
           OverloadTest.Method(123);
           // "int"
           OverloadTest.Method('hi hi');
           // "string"
       }
   }
   ```



#### 6. Class, Object, Instance, Interface?

1. 클래스(Class)
   - 객체를 만들어 내기 위한 설계도 또는 틀
   - 연관되어 있는 변수와 메서드의 집합
2. 객체(Object)
   - 소프트웨어 세계에서 구현할 대상
   - 클래스에 선언 된 모양 그대로 생성된 실체
   - 클래스의 인스턴스라고 부름
   - 객체는 모든 인스턴스를 대표하는 포괄적인 의미를 갖는다.

3. 인스턴스

   - 설계도를 바탕으로 소프트웨어 세계에 구현된 구체적인 실체
   - 즉, 객체를 소프트웨어에 실체화 하면 그것을 '인스턴스'라고 부른다.

4. 클래스 vs 객체

   - 클래스는 설계도 객체는 설계도로 구현한 모든 대상을 의미
   - 클래스 : 붕어빵기계, 객체 : 붕어빵

5. 추상 클래스

   - 완성되지 않은 메서드를 가지고 있는 클래스로 추상 메서드를 하나라도 가지고 있으면 추상 클래스가 된다.
   - 메서드가 미완성이라고 볼 수 있기 때문에, 추상클래스로는 개체를 생성 할 수 없다.

   ``` c#
   abstract class Animal
   {
       public string name;
       public abstract void Move(); // 추상 메서드
       // 동물이란 개체에서 동물이 날지, 기어다닐지 확정할 수 없으므로 추상메서드로 만듬
       
       public void Move2() // 일반 메서드
       {
           Console.WriteLine("동물이 움직임");
       }
   }
   
   class Dog : Animal
   {
       public override void Move() // 상위 클래스의 추상메서드를 오버라이드 시켜 사용
       {
           Console.WriteLine("네 발로 움직임");
       }
   }
   
   ```

5. 인터페이스

   - 추상 클래스 처럼 완성되지 않은 불완전한 것이지만, 추상 클래스 보다 추상화 정도가 높다.
   - 오직 추상 메서드와 상수만을 멤버로 가질 수 있다.
   - 인터페이스를 다른 클래스를 작성하는데 도움을 목적으로 작성된다

   ```c#
   interface ILogger // 인터페이스
   {
       void WriteLog(string log);
   }
   class consoleLogger : ILogger // 인터페이스를 구현한 클래스
   {
       public void WriteLog(string log)
       {
           Console.WriteLine("{0} {1}", DateTime.Now.ToLocalTime(), log)
       }
   }
   ```

   

6. 추상클래스 vs 인터페이스

   - 공통점
     - 스스로 객체를 생성 할 수 없다.
     - 상속 관계에서만 존재한다.
   - 추상 클래스는 클래스이므로 다중 상속을 할 수 없지만 인터페이스는 클래스가 아니기 때문에 다중상속이 허용된다.
   - 인터페이스는 일반메서드 및 변수를 가질 수 없다.

7. 

