## 랜덤으로 행 추출하기
- sample 함수를 이용한 데이터 랜덤 추출
- 특정 개수만큼 추출하기

    ```python
    import pandas as pd

    data = {
        'A' : ['apple', 'grape', 'pear', 'banana', 'orange'],
        'B' : [11, 19, 2, 7, 41]
    }
    df = pd.DataFrame(data)

    df
     A B
    0 apple 11
    1 grape 19
    2 pear 2
    3 banana 7
    4 orange 41
    ```

    ```python
    # 특정 개수만큼 추출하기
    df.sample(n=2)
          A	      B
    4	orange	  41
    2	pear	  2
    ```

    ```python
    df.sample(n=7, replace=True)
         A	      B
    1	grape	  19
    0	apple	  11
    1	grape	  19
    2	pear	  2
    3	banana	  7
    3	banana	  7
    2	pear	  2
    ```

- 특정 비율만큼 추출하기

    ```python
    # 20%
    df.sample(frac=0.2)
          A	      B
    2	pear	  2
    ```

    ```python
    # 200% 복원 추출
    df.sample(frac=2, replace=True)
          A	      B
    0	apple	  11
    2	pear  	  2
    2	pear	  2
    3	banana	  7
    3	banana	  7
    0	apple	  11
    2	pear	  2
    2	pear	  2
    1	grape	  19
    1	grape	  19
    ```