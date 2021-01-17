## 텍스트 파일(.txt) 불러오기 / 저장하기
1. 텍스트 파일 불러오기
    - 아래 텍스트가 저장된 파일 이름을 data.txt 라고 가정

        번호,이름,몸무게  
        1,Kim,70  
        2,Lee,90  
        3,Moon,55  
        4,Yoon,60  

    - read_table
        - 파일 이름을 포함한 경로를 넣어주고 sep 인자에는 구분자를 넣어 준다. sep 인자의 기본값은 탭('\t')

        ```python
        import pandas as pd

        # data.txt 파일이 저장된 경로 지정
        df = pd.read_table('./data.txt', sep=',')

        # 출력
        print(df)
            번호    이름  몸무게
        0   1   Kim   70
        1   2   Lee   90
        2   3  Moon   55
        3   4  Yoon   60

        ```

    - read_csv
        - sep 인자의 기본값은 쉼표라 생략 가능

        ```python
        import pandas as pd

        df = pd.read_csv('./data.txt')

        print(df)
          번호   이름  몸무게
        0   1   Kim   70
        1   2   Lee   90
        2   3  Moon   55
        3   4  Yoon   60
        ```

        - read_csv와 read_table의 차이점은 read_csv는 기본 구분자가 쉼표(,)이고 read_table은 기본 구분자가 탭(\t)이라는 차이만 있고 성능면에서는 차이가 없다.

    - 헤더가 없는 텍스트 파일 읽어오기 (파일 이름 data_no_header.txt 라고 가정)
        1,Kim,70  
        2,Lee,90  
        3,Moon,55  
        4,Yoon,60  

        ```python
        import pandas as pd

        df = pd.read_table('./data_no_header.txt', sep=',', header=None, names=['번호','이름','몸무게']

        print(df)
          번호   이름  몸무게
        0   1   Kim   70
        1   2   Lee   90
        2   3  Moon   55
        3   4  Yoon   60
        ```

        - 헤더가 없는 경우 header 인자에 None을 넣어주고, names를 이용하여 컬럼 이름을 지정해줘야 한다.
2. 데이터 프레임을 텍스트 파일로 저장하기
    - 데이터를 텍스트 파일로 저장하려면 to_csv 함수를 사용

        ```python
        import pandas as pd

        # 데이터 생성
        data = {
            '번호' : [1,2,3,4],
            '이름' : ['Kim', 'Lee', 'Moon', 'Yoon'],
            '몸무게' : [70, 90, 55, 60]
        }
        # 데이터 프레임 생성
        df = pd.DataFrame(data)
        # 인덱스 컬럼 저장하지 않음, 구분자는 탭으로 지정
        df.to_csv('test.txt', index=False, sep='\t')
        ```

    - 헤더(컬럼 이름) 제외하고 저장하기

        ```python
        import pandas as pd

        # 데이터 생성
        data = {
            '번호' : [1,2,3,4],
            '이름' : ['Kim', 'Lee', 'Moon', 'Yoon'],
            '몸무게' : [70, 90, 55, 60]
        }
        # 데이터 프레임 생성
        df = pd.DataFrame(data)
        # 인덱스 컬럼 저장하지 않음, 구분자는 탭으로 지정
        df.to_csv('test2.txt', header = None, index=False, sep='\t')
        ```