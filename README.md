# B---Non-square-Equation

#include<iostream>

using namespace std;

int s(long long x)
{

	string num = to_string(x);
	int R = 0;
	for (int i = 0; i < num.size(); i++)
	{
		R += (num[i] - '0');
	}
	return R;
}

int check(long long x, long long n)
{

	if (((x*x) + (s(x)*x)) == n)
		return 0;
	else if (((x*x) + (s(x)*x)) < n)
		return 1;
	else
		return 2;
}

int bs(long long n)
{

	long long s = 0, e = 1e10;
	while (s < e)
	{
  
		long long mid = s + (e - s) / 2;
		if (e - s <= 10000)
		{
			for (int i = s; i < e; i++)
			{
				if (check(i, n) == 0)
				{
					return i;
				}
			}
		}
		if (check(mid, n) == 0)
		{
			return mid;
		}
		else if (check(mid, n) == 1)
			s = mid + 1;
		else
			e = mid - 1;
	}
	return -1;
}


int main()
{

	long long n;
	cin >> n;
	if (bs(n) == (-1))
		cout << "-1";
	else
		cout << bs(n);
	return 0;
}
