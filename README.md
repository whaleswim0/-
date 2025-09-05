import pandas as pd
import matplotlib.pyplot as plt

# 웹에서 찾은 순천시 읍면동별 인구 데이터 (2025년 1월 기준, 나무위키 참고)
# 웹에서 직접 데이터를 가져올 수 없으므로, 검색 결과를 바탕으로 DataFrame을 수동으로 생성합니다.
# 실제 데이터는 더 많은 동을 포함하지만, 시각화를 위해 인구가 많은 상위 7개 동을 예시로 사용합니다.
data = {
    '읍면동명': ['왕조1동', '덕연동', '해룡면 신대출장소', '삼산동', '도사동', '왕조2동', '해룡면 상삼출장소'],
    '인구수': [43433, 39706, 32475, 28840, 16965, 16890, 18055]
}
df_suncheon = pd.DataFrame(data)

# '인구수' 기준으로 내림차순 정렬
df_suncheon = df_suncheon.sort_values(by='인구수', ascending=False)

# 파이 차트 시각화
plt.figure(figsize=(10, 10))

# 한글 폰트 설정 (Mac/Linux용)
# 폰트 경로를 시스템에 맞게 수정해야 할 수 있습니다.
plt.rcParams['font.family'] = 'AppleGothic'  # macOS
plt.rcParams['axes.unicode_minus'] = False # 마이너스 기호 깨짐 방지

# 파이 차트 그리기
plt.pie(
    df_suncheon['인구수'],
    labels=df_suncheon['읍면동명'],
    autopct='%1.1f%%',
    startangle=90,
    textprops={'fontsize': 12, 'color': 'black'},
    pctdistance=0.8,
    labeldistance=1.1,
    wedgeprops={'edgecolor': 'white', 'linewidth': 1.5}
)

# 차트 제목 설정
plt.title('순천시 주요 행정동별 인구 비율 (2025년 기준)', fontsize=16, pad=20)

# 파이 차트가 원형으로 보이도록 설정
plt.axis('equal')

# 그래프 표시
plt.show()
