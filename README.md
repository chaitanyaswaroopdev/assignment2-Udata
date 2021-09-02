# assignment2-Udata

# Chaitanya Swaroop Udata

## Paris

The **French** capital is one of the most **romantic** cities in Europe and one of the world's most visited cities. There are endless reasons to visit Paris repeatedly, it is a **beautiful** and **cultural** city, very walkable, with great sights, and it has been a source of inspiration for many **writers, artists, and filmmakers**.

---

# Travelling Directions
1. Maryville to Vishakapatnam(India)
    1. Maryville to Kansas City (MCI)
    2. Kansas City to Chicago (ORD)
    3. Chicago to San Fransico (SFO)
    4. San Fransico to New Delhi (IGI)
    5. New Delhi to Hyderabad (RGI)
    6. Hyderabad to Vishakapatnam (Domestic)

- Clothes
- Electronic Items
- Food Items
- Money
  
[AboutMe](https://github.com/chaitanyaswaroopdev/assignment2-Udata/blob/main/AboutMe.md)

---

# Food/Drink that I would recommend to my friend
| Food/Drink | Location | Price |
| :---: | :---: | :---: |
| Biryani | Paradise | $12 |
| Parota | Pista house | $15 |
| Maggie | DLF | $5 |
| shawarma | Hitechcity | $10 |
| Icecream | Creamstone | $3 |

---
# Pithy Quotes
>*"Truth can be stated in a thousand different ways, yet each one can be true."*<br/>
>*"Comfort is no test of truth. Truth is often far from being comfortable."*<br/>
> -by **Swami Vivekananda**

---
# Code Fencing 
>Dynamic programming is both a mathematical optimization method and a computer programming method. The method was developed by Richard Bellman in the 1950s and has found applications in numerous fields, from aerospace engineering to economics.

[Source Link for Description](https://en.wikipedia.org/wiki/Dynamic_programming)

```
int m, n;
vector<long long> dp_before(n), dp_cur(n);

long long C(int i, int j);

// compute dp_cur[l], ... dp_cur[r] (inclusive)
void compute(int l, int r, int optl, int optr) {
    if (l > r)
        return;

    int mid = (l + r) >> 1;
    pair<long long, int> best = {LLONG_MAX, -1};

    for (int k = optl; k <= min(mid, optr); k++) {
        best = min(best, {(k ? dp_before[k - 1] : 0) + C(k, mid), k});
    }

    dp_cur[mid] = best.first;
    int opt = best.second;

    compute(l, mid - 1, optl, opt);
    compute(mid + 1, r, opt, optr);
}

int solve() {
    for (int i = 0; i < n; i++)
        dp_before[i] = C(0, i);

    for (int i = 1; i < m; i++) {
        compute(0, n - 1, 0, n - 1);
        dp_before = dp_cur;
    }

    return dp_before[n - 1];
}

```
[Source link for code](https://cp-algorithms.com/dynamic_programming/profile-dynamics.html)