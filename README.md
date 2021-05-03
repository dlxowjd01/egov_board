# egov_board
egov_board java project

test3 브랜치에 push 했습니다. test3 브랜치를 받아야 합니다.

@Resource가 적용이 안되나 해서 <context:annotation-config />를 설정 파일에 추가해도 별차이가 없었습니다.

클래스로 직접 명시해서 서블릿 설정에 등록하는 방법을 써봐도 오류는 계속 되었습니다. 

@autowired로 바꿔보았는데 역시 오류가 생겨서 어노테이션 자체를 불러오지 못하는 문제는 아닌 것 같았습니다.

 <context:exclude-filter type="annotation" expression="org.springframework.stereotype.Service"/> 를 include로 다시 바꾸면 

컨트롤러 단에서 의존성 주입 오류 메세지는 사라지는데 대신 context-common에 정의된 bean인 leaveaTrace를 이용할수 없다고 나옵니다.

그후 메이븐 업데이트 빌드등을 해보았으나 별 차이가 없었고 leaveaTrace는 전자정부 프레임워크 실행환경 안에 포함되어 있다고 해서 라이브러리를 찾아봤는데 

egovframework.rte.fdl.cmmn에 해당하는 라이브러리가 존재하지 않아서 pom.xml에 설정 넣어주고 메이븐 다시 빌드했는데 메이븐이 오류가 생겼는지 갑자기 tomcat 서버가 사라지면서

이클립스 프로젝트 설정 자체가 이상하게 되버려서 지난 주말까지 작업한 내용으로 다시 커밋을 되돌린 상태로 깃허브에 올렸습니다.

leaveaTrace 라이브러리 등록을 다시한번 시도해보거나 서비스 구현 단에서 @Resource name="service"은 지정해줬는데 서블릿 설정파일에서 

<bean name="service" class="현재사용 패키지경로" /> 인 형태로 bean name을 지정해주지 않아서  @Resource 에서 name="service"를 못 읽어드리는게 아닌가하고 다음에는 이 부분을 

시도해보려고 합니다.


