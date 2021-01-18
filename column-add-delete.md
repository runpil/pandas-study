## 열 추가/삭제하기
- 열 추가하기

    ```python
    import pandas as pd

    # 데이터 생성
    data = {
        'id' : ['kim', 'lee', 'moon'],
        'age' : [37, 45, 33]
    }

    df = pd.DataFrame(data)

    # 기존 데이터에 'weight'이라는 열 추가하기
    df['weight'] = [75, 80, 55]
    df
        id  age  weight
    0	kim	 37	  75
    1	lee	 45	  80
    2	moon 33	  55
    ```

    ```python
    # insert 함수 이용하는 방법
    # 열을 원하는 위치에 넣고 싶을 때 사용
    # df.insert('순서 인덱스', '열 이름', 데이터리스트)
    import pandas as pd

    # 데이터 준비
    data = {
        'id' : ['kim', 'lee', 'moon'],
        'age' : [37, 45, 33]
    }

    df = pd.DataFrame(data)

    df.insert(0, 'weight', [75, 80, 55])
    df
        weight  id  age
    0	  75	  kim  37
    1	  80	  lee	 45
    2	  55	  moon 33
    ```

    ```python
    # assign 이용하기
    import pandas as pd

    data = {
        'id' : ['kim', 'lee', 'moon'],
        'age' : [37, 45, 33]
    }

    df = pd.DataFrame(data)

    # 맨 끝열에 열이 추가되지만 실제 데이터 프레임에는 추가되지 않는다.
    df.assign(weight = [75, 80, 55])
    df
        id	age
    0	kim	 37
    1	lee	 45
    2	moon 33

    # 새로운 열이 추가된 데이터를 변수에 넣어줘야 한다.
    df = df.assign(weight = [75, 80, 55])
    df
        id  age  weight
    0	kim	 37	  75
    1	lee	 45	  80
    2	moon 33	  55
    ```

- 열 삭제하기

    ```python
    # drop 함수 이용하기
    df.drop(['weight'], axis=1)
    id	age
    0	kim	37
    1	lee	45
    2	moon	33

    # 실제 삭제되지 않는다.
    df
        id  age  weight
    0	kim	 37	  75
    1	lee	 45	  80
    2	moon 33	  55

    # 삭제된 데이터 프레임을 얻고 싶다면 변수에 담아줘야 한다.
    df = df.drop(['weight'], axis=1)
    df
        id	age
    0	kim	 37
    1	lee	 45
    2	moon 33
    ```

    ```python
    # 필요 없는 열을 삭제한다는 말은 필요한 열만 추출하는 것과 같다.
    # 삭제해야 하는 열이 필요한 열보다 많을 때 이 방법이 더 편리
    df = df[['id']]
    df
        id
    0	kim
    1	lee
    2	moon
    ```