# Задача с codeforces:
https://codeforces.com/problemset/problem/2167/G
<img width="1285" height="183" alt="image" src="https://github.com/user-attachments/assets/cbb0541a-cc3c-4a67-9ada-1f1e92d307f4" />
Решение на c++
```
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

using ll = long long;
int main() {
    ios::sync_with_stdio(false);
    cin.tie(nullptr);

    int t;
    cin >> t;
    while (t--) 
    {
        int n;
        cin >> n;
        vector<ll> a(n, 0), c(n, 0);
        ll total_cost = 0;

        for (int i = 0; i < n; i++) 
            cin >> a[i];
        for (int i = 0; i < n; i++) 
        {
            cin >> c[i];
            total_cost += c[i];
        }

        vector<ll> dp(c);

        for (int i = 0; i < n; i++) 
        {
            for (int j = 0; j < i; j++) 
            {
                if (a[j] <= a[i]) 
                { 
                    if (dp[j] + c[i] > dp[i]) 
                    {
                        dp[i] = dp[j] + c[i];
                    }
                }
            }
        }

        ll max_keep = *max_element(dp.begin(), dp.end());
        cout << total_cost - max_keep << '\n';
    }

    return 0;
}
```
Идея в том, чтобы не искать лучшие комбинации для минимизации трат на изменения, а максимизировать экономию на тех, кого нам предпочтительнее оставить. Т.е. в dp мы пытаемся хранить сумму тех элементов, которые не хотим менять в силу дороговизны изменения их последовательности. Итоговая стоимость = изначальная стоимость - стоимость экономии

Задачи №1 и №3 с визуализацией будут представлены отдельным Jupyter-ноутбуком
