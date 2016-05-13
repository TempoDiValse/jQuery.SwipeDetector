# jQuery.SwipeDetector
Detect Swipe Event on Mobile for jQuery

Swipe 방향이 어느 방향인지를 알려줍니다.

	사용방법:
		- 초기화
		$(OBJECT).detect({ JSON }); or $(OBJECT).detect();

		- 함수 호출
		$(OBJECT).detect('Methods', var_args); 
	
	API:
		- init
			초기화 함수로 굳이 콜 하지 않고 detect()에 JSON이나 아무것도 안 넘겨줘도 실행이 됌.

		- setOption
			옵션 설정은 개별적으로 한다.

		- options {
			threshold(int) : 화면에서 Swipe 이벤트를 일으키게 해주는 기준으로 화면 사이즈에서 threshold 값을 나눈 값입니다.
			exceptArea(array) : Swipe 이벤트에서 제외할 대상의 "ID값" 만 넣습니다.
			callback(Function) : Swipe한 방향을 콜백 받습니다.
				@return direction(String) 방향을 전달하고 값은 DirectionType 항목을 참조한다. 			
		}
