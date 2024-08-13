Maximum profit by buying and selling a share atmost twice in C
Here, in this page we will discuss the program to find maximum profit by buying and selling a share atmost twice in C .
We are giving with the price[] and we need to maximize the profit by selling the product at most two times. If the trader is allowed to make at most 2 transactions in a day, whereas the second transaction can only start after when the first transaction is completed Buy->Sell->Buy->Sell. 

Example :

Input : price[7] ={ 2, 30, 15, 10, 8, 25, 80 }
Output : Maximum-Profit = 100
Explanation : If the trader first buy the share at price of 2 and then sell the share  at price 30 so in first transaction he made the profit of 28 , Again he buy the share at price 8 and then sell the share at price 80 so second time he made the profit of 72. Hence from both the transaction he get the profit of 100 which is the maximum value.
Maximum profit by buying and selling a share atmost twice in C
Method 1 :
Take the size of the array from the user and store it n variable say n.
Declare an array price of size n and take all elements of the price array from the user.
Create a max function that return the maximum value of that pass to it.
Create an array say profit of size n and initialize all its value to 0.
Now, run a loop from N-1 to 0 (i.e, from right to left) and update profit[i] such that profit[i] stores maximum profit achievable from one transaction in sub-array price[i..n-1].
Run a loop from 0 to n-1 in price[] from left to right and update profit[i] such that profit[i] stores maximum profit such that profit[i] contains maximum achievable profit from two transactions in sub-array price[0..i].
After completing the iteration return value of profit[n-1].
Time-Space Complexities :
Time – complexity : O(n)
Space – complexity : O(n)
Maximum profit in C
Code to find Maximum profit by buying and selling a share atmost twice in C
#include<stdio.h>

int max(int a, int b){
   if(a>b)
     return a;
   return b;
}

int maxProfit(int price[], int n)
{
   int profit[n];
   for (int i = 0; i < n; i++)
     profit[i] = 0;

   int max_price = price[n - 1];
   for (int i = n - 2; i >= 0; i--) {
       if (price[i] > max_price)
       max_price = price[i];
       profit[i] = max(profit[i + 1], max_price - price[i]);
   }

   int min_price = price[0];
   for (int i = 1; i < n; i++) {
      if (price[i] < min_price)
         profit[i] = max(profit[i - 1],profit[i] + (price[i] - min_price));
   }
   int result = profit[n - 1];
   return result;
}

// Driver code
int main()
{ 
   int n;
   scanf("%d", &n);

   int price[n];
   for(int i=0; i<n; i++) scanf("%d", &price[i]);
   printf("Maximum Profit = %d", maxProfit(price, n));
   return 0;
}
Input : 

7

2, 30, 15, 10, 8, 25, 80 

Output :

maximum Profit = 100

Related Pages
Given an array which consists of only 0, 1 and 2

Find the “Kth” max and min element of an array

Find the Union and Intersection of the two sorted arrays

Find Largest sum contiguous Subarray

Minimize the maximum difference between heights 

Method 2 :
Create  a max function that will return the maximum of the value that pass to it.
Create four variables for taking care of the first buy, first sell, second buy, second sell.
And Set first buy and second buy as INT_MIN and first and second sell as 0.
This is to ensure to get profit from transactions.
Iterate through the array and return the second buy as it will store maximum profit.
Time-Space Complexities :
Time – complexity : O(n)
Space – complexity : O(1)
Code to find Maximum profit by buying and selling a share atmost twice in C
#include<stdio.h>

int max(int a, int b){
   if(a>b)
     return a;
   return b;
}

int maxProfit(int price[], int n)
{
   int first_buy = INT_MIN;
   int first_sell = 0;
   int second_buy = INT_MIN;
   int second_sell = 0; 
   for(int i=0;i<n;i++) { 
     first_buy = max(first_buy,-price[i]);
     first_sell = max(first_sell,first_buy+price[i]);
     second_buy = max(second_buy,first_sell-price[i]);
     second_sell = max(second_sell,second_buy+price[i]);
   }
   return second_sell;
}




// Driver code
int main()
{ 
   int n;
   scanf("%d", &n);

   int price[n];
   for(int i=0; i<n; i++) scanf("%d", &price[i]);
   printf("Maximum Profit = %d", maxProfit(price, n));
   return 0;
}
Input : 

7

2, 30, 15, 10, 8, 25, 80 

Output :

maximum Profit = 100

Prime Course Trailer

Related Banners
Get PrepInsta Prime & get Access to all 200+ courses offered by PrepInsta in One Subscription

Get Prime
While loop in C
