<h1>마케팅 관리 과제 데이터 분석</h1>

<p> JAPAN GDP 파일과 굉장히 유사한 분석이다. JAPAN파일에서 기술적인 부분을 더욱 자세히 볼 수 있을 것이다.</p>

<h1>개요</h1>
구글 트렌드 검색수를 이용해서 숏폼 플랫폼 TikTok의 성장을 예측해본다. 하지만 단순 TikTok 분석만이 아니라 Facebook과 Instagram을 연관시켜 분석을 해본다. 그리고 Tiktok의 SWOT분석과 STP를 제안한다.


<h1>분석 방법</h1>
http://www.reacademy.org 전국 부동삭학회에서 분석한 전세가격 예측, 검색 지수를 이용해서 사업의 상태를 분석하는 것은 필수로 여긴다. 2017년 한국에 론칭한 TikTok은 2019년 최고 다운로드 수를 달성했다. 하지만 현재 2021년까지 개인정보보안, 중국에 대한 불신이 증가하며 TikTok이라는 브랜드 가치가 떨어지기 시작했다. 그래서 구글 트렌드 검색지수를 이용해 대한민국 내에서 TikTok 발전 가능성을 예상해본다. <br>
사용할 언어는 Python3 3.6.5버전으로 사이킷런을 이용한다. 그다음 정규화를 통해 -1~1사이의 값이 나오도록한다. 
```python
def min_max_normalize(lst):
    normalized = []
    
    for value in lst:
        normalized_num = (value - min(lst)) / (max(lst) - min(lst))
        normalized.append(normalized_num)
 return normalized
```

위 코드가 정규화 방법이다.

<h1>분석 과정</h1>

```python
df=pd.read_csv("https://raw.githubusercontent.com/cjfghk5697/Marketing_analysis/main/csv/Tiktok%EA%B2%80%EC%83%89%EC%96%B4.csv")
X= df["week"]
y = df["Tiktok(en)"]
X=pd.to_datetime(X)

X=X.map(dt.datetime.toordinal)

y=min_max_normalize(y)
plt.plot(X, y, 'o')
plt.ylabel("Tiktok")
line_fitter = LinearRegression()
line_fitter.fit(X.values.reshape(-1,1), y)
plt.plot(X, y, 'o')
plt.plot(X,line_fitter.predict(X.values.reshape(-1,1)))
plt.show()
print("Tiktok:",line_fitter.coef_)
```
분석 코드이다. 간단한 분석 기법이다. df에 엑셀 파일이 들어가고 X에는 주기 Y에는 검색 횟수가 들어간다. 그래서 Y를 정규화 시킨다.

<br>
![tiktok영어](https://user-images.githubusercontent.com/80466735/120789355-7da46e00-c56c-11eb-9629-954a548c6418.PNG)<br>
사진 1 한국 내에서 Tiktok 검색횟수<br>
 ![tiktok한국어](https://user-images.githubusercontent.com/80466735/120789363-7ed59b00-c56c-11eb-975e-8fb79929adf4.PNG)<br>
사진 2 한국 내에서 틱톡 검색횟수
전체적으로 기울기는 양의 값을 가지고있다. 하지만 기울기 값이 작아서 전과 같은 성장은 없을 것으로 보인다. 아마도 현재 상태 유지를 하게 될 수있다.
<br>
하지만 이 틱톡 사례로는 부족하다. 그래서 페이스북과 인스타그램 사례를 추가해서 근거를 강화하고자 한다.

<h1>추가 분석</h1>
위에까지 내용은 전에 한 Japan GDP Analysis와 다름이 없다. 이번에 1학년 1학기때 배우는 경영통계를 활용해 오직 기울기만 이용하는 게 아닌 더욱더 체계적으로 분석해 볼 것이다.<br>

<h1>결론</h1>
마케팅 관리 pdf다. 여기에 SWOT, 4P, SOLUTION, STP가 다 들어가 있다. 자료 공유를 허용해준 마케팅 관리 팀원에게 정말 감사하다.
[Marketing Management Final Presentation.pdf](https://github.com/cjfghk5697/Marketing_analysis/files/6617453/Marketing.Management.Final.Presentation.pdf)<br>




