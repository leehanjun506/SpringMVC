## @Controller(자동 빈 등록) 는 반환값이 string이면 뷰 이름으로 인식 되서 뷰를 찾고 뷰가 랜더링 됨
</br>

## @RequestMapping 은 uri 매핑하는 어노테이션이다.
</br>

## @RestController는 반환 값으로 http메시지 바디에 바로 입력한다.
### 보통 Rest API를 만들 때 사용되는 컨트롤러이다.
</br>

## @ResponseBody 반환값을 http 응답메세지에 넣어서 반환
</br>

## @RequestParam String name{요청파라미터 사용 가능}
</br>

## @RequestParam(required = false) int age -> 파라미터 생략 가능
</br>

### (null 입력할 경우 500예외 발생 -> Integer로 변경

### defaultValue 를 어노테이션 인자에 추가해주면 기본 값 적용 가능

### 파라미터는 Map으로도 조회 가능
</br>

## @ModelAttribute 적용 !!

### public String modelAttribute(@ModelAttribute HelloData helloData) {}
### -> 모델 어트리뷰트 어노테이션이 있으면 HelloData 객체를 생성후 요청 파라미터의 이름으로 HelloData객체의 프로퍼티를 찾는다. 그리고 해당 프로퍼티의 setter호출해서 파라미터의 값 입력(바인딩)한다.
### 파라미터 이름이 username이면 setUsername() 메서드를 찾아서 호출하면서 값 입력
### 숫자가 들어갈 곳에 문자가 들어가는 경우 바인딩 오류가 일어나 이러한 부분은 검증해줘야함.

## HTTP 요청 메시지 단순 텍스트
### @RequestBody를 사용하면 HTTP 메시지 바디 정보를 편리하게 조회 할 수있다.
### 헤더 정보는 @RequestHeader 사용

### @ResponseBody를 사용하면 응답 결과를 HTTP메시지 바디에 직접 담아서 전달 가능 이 경우에 view 사용 x
</br>

## HTTP 요청 메시지 JSON

### HTTP 요청시에 content-type 이 application/json여야 JSON을 처리할 수 있는 HTTP 메시지 컨버터가 실행된다.
### @RequestBody는 생략하게 되면 객체에서 @ModelAttribute가 적용되어 요청 파라미터를 처리하게 된다.

    @ResponseBody
    @PostMapping("/request-body-json-v5")
    public HelloData responseBodyJsonV5(@RequestBody HelloData helloData) {
        log.info("username={}, age={}", helloData.getUsername(), helloData.getAge());

        return helloData;
    }
helloData에 맞는 json요청을 받아 @ResponsBody를 사용해 json을 반환해준다.
