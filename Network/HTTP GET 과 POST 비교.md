# HTTP 의 GET 과 POST 비교
> 둘 다 HTTP 프로토콜을 이용해서 서버에 무엇인가를 요청할 때 사용하는 방식이다. 하지만 둘의 특징을 제대로 이해하여 기술의 목적에 맞게 알맞은 용도에 사용해야 한다.

<br><br><br>

## GET
- 요청하는 데이터가 `HTTP Request Message` 의 `Header` 부분에 `URL` 이 담겨서 전송된다.
- `URL` 상에 `?` 뒤에 데이터가 붙어 Request 를 보내게 된다.
- `URL` 이라는 공간에 담겨가기 때문에 전송할 수 있는 데이터의 크기가 제한적이다. 또한, 보안이 필요한 데이터에 대해서는 데이터가 `URL` 에 그대로 노출되므로, GET 방식은 적절하지 않다. (ex. password)
<br><br>

## POST
- 요청하는 데이터가 `HTTP Request Message` 의 `Body` 부분에 데이터가 담겨서 전송된다.
- 바이너리 데이터를 요청하는 경우 POST 방식으로 보내야 하는 것처럼, **데이터 크기**가 GET 방식보다 크고 **보안**면에서 낫다.
<br><br>

## GET 과 POST 의 사용
- `GET` 가져오는 것이다. 서버에서 어떤 데이터를 가져와서 보여준다거나 하는 용도이지 **서버의 데이터를 변경하지 않는다.**
- 반면에 `POST` 는 **서버에 데이터를 추가 혹은 수정** 하기 위해서 사용된다.
- `GET` 방식의 요청은 브라우저에서 `Caching` 할 수 있다. 때문에 `POST` 방식으로 요청해야 할 것을, 보내는 데이터의 크기가 작고 보안적인 문제가 없다는 이유로 `GET` 방식으로 요청한다면, **기존에 `Caching` 되었던 데이터가 응답될 가능성이 존재한다.**
