C++ Coding Style
====

파일 네이밍
----
* 파일 이름에는 영문자와 언더바 조합을 사용한다.
* 모든 띄어쓰기는 언더바로 대체한다.
* 소스 파일은 .cpp를, 헤더 파일은 .h 확장자를 사용한다.
* 파일 이름은 namespace와 class명의 조합으로 한다.
  - 최상위 네임스페이스는 생략한다.
  - 예) io_tcp_socket.cpp

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
  
클래스 정의
----
* 메소드 인라이닝을 사용하지 않는다.
  - 1줄짜리 단순한 getter/setter 코드일지라도 cpp파일에 작성한다.
* 
