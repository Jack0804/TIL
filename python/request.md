# Python3 Request 파일전송

## request 전송
### Post방식으로 파일(데이터) 및 문자열 전송을 알아본다.

### `send_file.py`    

```python
# request를 import한다. (import방법은 여러종류이므로 검색활용)
import reqeust

#보내고자하는 파일을 'rb'(바이너리 리드)방식 열고
files = open('/home/pi/test/test.txt', 'rb')

# 파이썬 딕셔너리 형식으로 file 설정
upload = {'file':files}
# String 포맷
obj={"temperature":'23.5', "humidity":'54.5'}

# request.post방식으로 파일전송.
res = requests.post('http://127.0.0.1:8080/test', files = upload, data = obj}
```

###전송방식은 미리 구현을했으나 오늘 알게된 흥미로운 사실,
- 파일의 경우 전송 할 때, `requests.post('http://127.0.0.1:8080/test', files = upload, data = obj}` 여기부분에서 
- `files = upload` 이 부분에서 `파일`을 보낼때는 `files` 라고 반드시 설정해주어야한다.
- `String(문자열)`을 보낼때는 'data' 로 설정해주어야한다.
    





    
    
    

