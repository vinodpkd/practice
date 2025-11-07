//P2.cpp : Program to find the smallest and largest number in an array.
//https://github.com/bpbpublications/Comprehensive-Data-Structures-and-Algorithms-in-C-Plus-Plus/blob/main/Chapter%2002/P2.cpp

```cpp
#include<iostream>
using namespace std;

int main()
{
	int arr[10] = {2,5,4,1,8,9,11,6,3,7};
	int small, large;

	small = large = arr[0];

	for(int i=1; i<10; i++)
	{
		if(arr[i] < small)
			small = arr[i];
		if(arr[i] > large)
			large = arr[i];
	}

	cout << "Smallest = " << small << ", Largest = " << large << "\n";

	return 0;
}//End of main()
```

Great question! The line `small = large = INT_MIN;` is **not required** in your original program — and in fact, it would be **incorrect** for your current logic.

small = large = INT_MIN; is required or not
### ✅ Why `small = large = arr[0];` is correct
- You're initializing both `small` and `large` to the **first element** of the array.
- This ensures that comparisons start from a valid value **within the array**.
- It works for **any array content**, including negative numbers.

### ❌ Why `INT_MIN` is not appropriate here
- `INT_MIN` is the **minimum possible value** for a 32-bit integer (typically −2,147,483,648).
- If you set `small = INT_MIN`, then no array element will ever be smaller — so `small` will remain `INT_MIN`, which is wrong.
- Similarly, setting `large = INT_MIN` is fine **only if** you're sure all array values are greater than `INT_MIN`, but it's unnecessary and risky.

### 🔄 When might you use `INT_MIN` or `INT_MAX`?
You might use them in **other contexts**, like:
```cpp
int largest = INT_MIN;
int smallest = INT_MAX;
```
This is useful when:
- You're scanning an array and want to ensure any real value will override the initial extreme.
- You're not initializing from the array itself (e.g., reading values from input).

But in your case — where the array is already initialized — using `arr[0]` is the safest and cleanest approach.

Would you like to see how this logic changes if you're reading array values from user input instead?

//P3.cpp : Program to reverse the elements of an array.

```cpp
#include<iostream>
using namespace std;

int main()
{
	int arr[10] = {1,2,3,4,5,6,7,8,9,10};
	int i,j,temp;

	cout << "The array is :\n";
	for(i=0; i<10; i++)
		cout << arr[i] << " ";
	cout << "\n";

	for(i=0,j=9; i<j; i++,j--)
	{
		/*
		temp = arr[i];
		arr[i] = arr[j];
		arr[j] = temp;
		*/
		std::swap(arr[i],arr[j]);
		/*
		#include <algorithm>
		std::vector<int> a{1,2,3,4,5,6,7,8,9,10};
  		std::reverse(a.begin(), a.end());
  */
	}

	cout << "After reversing, the array is :\n";
	for(i=0; i<10; i++)
		cout << arr[i] << " ";
	cout << "\n";

	return 0;
}//End of main()
```

//P5.cpp : Program to understand the effect of passing an array to a function.

```cpp
#include<iostream>
using namespace std;

void func(int val[])
{
	int sum=0;

	for(int i=0; i<6; i++)
	{
		val[i] = val[i]*val[i];
		sum += val[i];
	}

	cout << "Sum of square = " << sum << "\n";

}//End of func()

int main()
{
	int arr[6] = {1,2,3,4,5,6};

	cout << "The array is :\n";
	for(int i=0; i<6; i++)
		cout << arr[i] << " ";
	cout << "\n";

	func(arr);

	cout << "Now the array is :\n";
	for(int i=0; i<6; i++)
		cout << arr[i] << " ";
	cout << "\n";

	return 0;
}//End of main()
```
Array got changed. 
