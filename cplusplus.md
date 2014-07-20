C++ Coding Style
====

파일 네이밍
----
* 파일 이름에는 영문자와 언더바 조합을 사용한다.
* 모든 띄어쓰기는 언더바로 대체한다.
* 소스 파일은 .cpp를, 헤더 파일은 .h 확장자를 사용한다.
* 파일 이름은 namespace와 class명의 조합으로 한다.
  - 최상위 네임스페이스는 이름은 생략한다.
  - 예) io_tcp_socket.cpp



네이밍
----
* 프레임워크나, 엔진을 사용할 경우에는 아래의 규칙보다는 해당 코드의 네이밍 규칙을 따른다.
* camel-case를 사용한다.
  - 클래스, 구조체, 상수, 열겨형의 이름은 첫 글자가 대문자로
  - 변수, 메소드의 이름은 첫 글자가 소문자로
  - 예) sendBufferSize, MyFileClass
* 매크로에는 대문자와 언더바만 사용한다.
* vector, array, list등의 컨테이너의 인스턴스 이름 뒤에는 s를 붙인다.
  - 예) vector monsters;
  - 예) list connections;
* 컨테이너의 수량을 나태내는 변수에는 앞에 n을 붙인다.
  - 예) int nWorkers;
* length 대신 len을 사용한다.
* size는 바이트 사이즈를 나타낼 때, len은 길이를 나타낼 때 사용한다.
  - string.size() != string.length()


주석
----
* 주석은 //보다 /**/를 사용한다.
* 로직을 설명하는 주석일 경우 코드의 바로 윗줄에 위치시킨다.
  - 세미콜런 오른쪽에 위치시킬 경우 코드가 가로로 길어지게 됨.
* 변수나 프로퍼티에 대한 설명일 경우에는 세미콜론 오른쪽에 위치시킨다.


키워드
----
* 템플릿에 class대신 typename을 사용한다.
  - 예)
  ```C++
  template <typename T>
  ```
* 지원하는 경우, NULL대신 nullptr을 사용한다.
* 경우와 판단에 따라 goto 키워드를 사용한다.
  - 단, 위로 역행하는 점프를 수행하는 goto는 사용하지 않는다.
* try, catch, throw는 사용하지 않는다.
* sizeof연산자는 괄호와 같이 사용한다.
* sizeof연산자에 변수 이름 대신 변수 타입을 넣는다.
  - sizeof(a)  (X)
  - sizeof(int)  (O)
* for each는 사용하지 않는다.
  - c++11의 Range-based for표준을 사용.
* new대신 new(nothrow)를 사용한다.


헤더 파일
----
* 모든 헤더 파일에는 define 가드 혹은 pragma once를 사용한다.
  - define 가드의 이름은 _파일이름_H
  - 일관성만 유지한다면 define 가드나 pragma once 어떤 쪽을 사용해도 관계 없지만, 한 프로젝트에서 두가지를 섞어서 사용하면 안된다.
* 가능한 경우 include를 피하고 포워드 선언을 사용한다.
* 헤더 파일에 using namespace 를 사용하지 않는다.
* 헤더 파일에 변수 선언을 하지 않는다.
* 상수는 namespace로 스코핑하여 정의한다.
  - define은 매크로 용도로만 사용.


클래스 정의
----
* 클래스 이름은 네임스페이스 이름이랑 중첩되지 않도록 작성한다.
  - Graphic::GraphicDriver (X)
  - Graphic::Driver (O)
* 다중 상속을 사용하지 않는다.
* 소멸자는 가상 함수로 선언한다.
* 클래스 내의 선언 순서는 friend -> enum -> (public,protected,private) methods -> (public,protected,private) properties
* 접근 지정자 아래 줄은 공백으로 두지 않는다.
* 관련 있는 메소드, 프로퍼티끼리 묶어서 정의한다, 묶음 아래는 한칸을 빈 줄로 둔다.
* 관련 있는 메소드, 프로퍼티 묶음에서 순서 흐름이 있을 경우 순서에 맞게 배치한다.
* 메소드 인라이닝을 사용하지 않는다.
  - 1줄짜리 단순한 getter/setter 코드일지라도 cpp파일에 작성한다.
* 파라미터 목록이 없을 경우에는 func(void) 대신 func()을 사용한다.
* 이름 앞에 _이 붙은 메소드는 public으로 선언하지 않는다.
  - 예)
  ```C++
  private:
    void _setZOrder(int z);
  ```

클래스 구현
----
* 생성자, 소멸자 안에 로직을 작성하지 않는다.
  - 생성자, 소멸자는 값을 반환할 수 없다 -> 예외에 대한 처리를 할 수 없기 때문에.
* 값 대입 대신에 생성자의 초기화 리스트를 사용한다.
* 생성자의 초기화 리스트에서는 연관 있는 프로퍼티끼리 묶음 지어서 줄 바꿈을 사용한다.
  - 예)
  ```C++
  Monster::Monster() :
    texture(nullptr),
    hp(0), maxHp(0),
    mp(0), maxMp(0),
    level(0){

  }
  ```
* 생성자의 초기화 리스트나, 인수 목록에서 줄 바꿈을 사용한 경우 첫 줄은 빈 줄로 한다.
  - 예)
  ```C++
  void Monster::someFooMethod(
    const string &foo, const string &bar,
    int value1, float value2){

    /* write here */
  }
  ```
소스 코드
----
* 한 줄이 80글자가 넘지 않도록 적절히 줄 바꿈을 사용한다.
* 줄 바꿈울 할 시에는 관련있는 단위로 묶는다.
  - 메소드 첫번째 인자 목록의 앞이나, r-value의 앞에서도 줄을 바꾼다.
  - 예)
  ```C++
    printf(
      "오늘은 %d년 %d월 %d일, %d시 %d분 %d초입니다.\n",
      year,month,date,
      hour,minute,second);
  ```
  ```C++
    int fooBarVariable =
      getFooBarValueFromSomewhere();
  ```
* 연산자 좌우로는 한 칸씩 띄운다.
  - 예) a += b
* 포인터의 애스터리스트(*)는 변수 이름의 바로 앞에 위치시킨다.
  - 예) int *ptr;
* 에일리어스의 앰퍼샌드(&)는 변수 이름의 바로 앞에 위치시킨다.
  - 예) int &v
