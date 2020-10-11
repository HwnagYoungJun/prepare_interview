# Design Pattern

## 1. 개요

> 일종의 설계 기법이며, 설계 방법이다.

### 목적

- SW 재사용성, 호환성, 유지 보수성을 보장



### 특징

- 디자인 패턴은 아이디어임, 특정한 구현이 아니다.
- 프로젝트에 항상 적용해야 되는 것은 아니지만, 추후 재사용, 호환, 유지 보수 시 발생하는 문제 해결을 에방하기 위해 패턴을 만들어 둔 것임.



### 원칙

- 객체지향 설계원칙 참조 (SOLID)



### 분류

> 3가지 패턴의 목적을 이해하자!

1. 생성 패턴 (Creational): 객체의 생성 방식 결정

   Class-crational patterns, Object-creational patterns

2. 구조 패턴 (Structual): 객체간의 관계를 조직

   > 2개의 인터페이스가 서로 호환이 되지 않을 때, 둘을 연결 해주기 위해서 새로운 클래스를 만들어서 연결시킬 수 있도록 함.

3. 행위 패턴 (Behavioral): 객체의 행위를 조직, 관리, 연합

   > 하위 클래스에서 구현해야 하는 함수 및 알고리즘들을 미리 선언하여, 상속 시 이를 필수로 구현 하도록 함



## 2. 패턴 종류

### 1. 싱글톤(Singleton)

> 생성 패턴, 애플리케이션이 시작될 때, 어떤클래스가 최초 한 번만 메모리를 할당(static)하고 해당 메모리에 인스턴스를 만들어 사용하는 패턴

- 싱글톤 패턴은 '하나'의 인스턴스만 생성하여 사용하는 디자인 패턴이다.
- 즉, 인스턴스가 필요할 때, 똑같은 인스턴스를 만들지 않고 기존의 인스턴스를 활용하는 것



### 2. 팩토리 메서드(Factory Method) 

> 하위 클래스에게 클래스의 인스턴스를 만드는 일을 맡김

```C#
public abstract class Unit
{
    public string m_strName;
    public int m_intAttackPower;
    public int m_intHealth;
    
    public abstract void Move(string _strPoint);
    public abstract void Attacked(ref Unit _unitTarget);
}

public class Marine : Unit
{
    public Marine(string _strName)
    {
        this.m_strName = _strName;
        this.m_intAttackPower = 5;
        this.m_intHealth = 45;
        Console.WriteLine(_strName + " : 생성 완료")
    }
    public override void Move(string _strPoint)
    {
        Console.WriteLine(m_strName + " : " + _strPoint + " 이동 완료");
    } 
}

public class Dropship : Unit
{
    public Dropship(string _strName)
    {
        this.m_strName = _strName;
        this.m_intAttackPower = 0;
        this.m_intHealth = 100;
        Console.WriteLine(_strName + " : 생성 완료")
    }
    public override void Move(string _strPoint)
    {
        Console.WriteLine(m_strName + " : " + _strPoint + " 이동 완료");
    }
}
```