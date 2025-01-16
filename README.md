# day10
def max_profit(N, consultations):
    # dp[i]는 i일에 퇴사 전까지 얻을 수 있는 최대 수익
    dp = [0] * (N + 1)

    for i in range(N - 1, -1, -1):
        Ti, Pi = consultations[i]  # 상담 걸리는 일수 Ti, 상담 수익 Pi
        if i + Ti <= N:
            dp[i] = max(dp[i + 1], Pi + dp[i + Ti])  # 상담을 할 경우
        else:
            dp[i] = dp[i + 1]  # 상담을 할 수 없는 경우

    return dp[0]

# 입력 처리
N = int(input())
consultations = [tuple(map(int, input().split())) for _ in range(N)]

# 결과 출력
print(max_profit(N, consultations))
