# Fast api study

## Install and Settings
```bash
pip install fastapi

pip install 'uvicorn[standard]'
```

### pipenv 
```bash
# 가상환경 설정 및 설치?
pipenv install fastapi uvicorn

# 가상환경 접속
pipenv shell
```

### pyenv + venv
```bash
# 3.11.2 환경의 파이썬 설치
pyenv install 3.11.2

# 3.11.2 사용
pyenv local 3.11.2

# 그 버전으로 venv 가상환경 생성
python -m venv venv
source venv/bin/activate

# 필요한 패키지 설치
pip install fastapi uvicorn

```

## Run
```bash
# --reload: 코드 변경시 리로딩
uvicorn main:app --reload
```


### Uvicorn
`pip install 'uvicorn[standard]'`
- uvicorn: An ASGI web server implementation for Python.
- ASGI: Asynchronous Server Gateway Interface (비동기 web server)
- [standard]: 최소한의 디펜던시로 설치
- async / await 구문을 사용
![alt text](image.png)

### Pydantic
- 데이터 유효성 검사(Validation)와 설정 관리(Settings Management)를 위해 사용하는 라이브러리
- 타입 힌트(type annotation)를 활용해 데이터의 구조와 타입을 명확하게 정의
- 실제 데이터가 이 구조와 타입을 만족하는지 런타임에서 자동으로 검사

```py
from fastapi import FastAPI 
from pydantic import BaseModel 

app = FastAPI()

class DataInput (BaseModel):
  name: str
class PredictOutput (BaseModel):
  prob: float prediction: int

@app.post("/pydantic", response_model=PredictOutput)
def pydantic_post(data_request: DataInput):
  return {"prob": 0.1, "prediction" : 0}
```

### Docs
- swagger: http://127.0.0.1:8000/docs
- redoc: http://127.0.0.1:8000/redoc



### Ref
- env: https://yubi5050.tistory.com/237
- 