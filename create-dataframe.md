## DataFrame 생성하기
1. 열(column)을 이용하여 데이터 만들기

    ```python
    import pandas as pd

    # 데이터 초기화
    df = pd.DataFrame()

    # 만들고자 하는 열의 이름과 데이터를 이용하여 열 데이터 생성
    df['id'] = [1, 2, 3, 4]
    df['name'] = ['Kim', 'Lee', 'Moon', 'Yoon']
    df['weight'] = [70, 90, 55, 65]

    # 출력
    print(df)
            id  name  weight
    0   1   Kim      70
    1   2   Lee      90
    2   3  Moon      55
    3   4  Yoon      65
    ```

2. 행(row)을 이용하여 데이터 만들기

    ```python
    import pandas as pd

    # 데이터 초기화 - 열 이름 지정
    df = pd.DataFrame(columns=['id', 'name', 'weight'])

    # 열 이름에 대응하는 행 데이터 생성
    df.loc[0] = [1, 'Kim', 70]
    df.loc[1] = [2, 'Lee', 90]
    df.loc[2] = [3, 'Moon', 55]
    df.loc[3] = [4, 'Yoon', 65]

    # 출력
    print(df)
        id  name  weight
    0  1   Kim     70
    1  2   Lee     90
    2  3  Moon     55
    3  4  Yoon     65
    ```

3. 딕셔너리(dictionary)를 이용하여 데이터 만들기

    ```python
    import pandas as pd

    # {열 : 데이터} 형식으로 딕셔너리 생성
    data = dict()
    data['id'] = [1, 2, 3, 4]
    data['name'] = ['Kim', 'Lee', 'Moon', 'Yoon']
    data['weight'] = [70, 90, 55, 65]

    # 만들어진 딕셔너리를 이용하여 데이터 초기화
    df = pd.DataFrame(data)

    # 출력
    print(df)
        id  name  weight
    0   1   Kim      70
    1   2   Lee      90
    2   3  Moon      55
    3   4  Yoon      65
    ```