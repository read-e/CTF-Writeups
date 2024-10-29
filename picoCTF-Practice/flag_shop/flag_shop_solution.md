# flag_shop
Liam Reidy

**Instructions:** There's a flag shop selling stuff, can you buy a flag? [Source] Connect with nc jupiter.challenges.picoctf.org 9745.

We are given a C program that is running on a nc server we can connect to. The server is a "flag store" where you can buy flags. Viewing the source code, we see that there are only two ways to interact with the shop. We can buy a fake flag with the amount of money ew start with, or we can buy the real flag, but we don't have enough funds.

Since the only way we can interact with the program is by buying the fake flag, the solution has something to do with that. Here's the part of the program that lets us buy the fake flag:
```c
scanf("%d", &number_flags);
if(number_flags > 0){
    int total_cost = 0;
    total_cost = 900*number_flags;
    printf("\nThe final cost is: %d\n", total_cost);
    if(total_cost <= account_balance){
        account_balance = account_balance - total_cost;
        printf("\nYour current balance after transaction: %d\n\n", account_balance);
    }
    else{
        printf("Not enough funds to complete purchase\n");
    }
}
```

The number of flags must be positive, so we can't cheese it that way. However, we can perform integer overflow on this line:
```c
total_cost = 900*number_flags;
```
If we use a number large enough, then total_cost will be negative. Then, in the following if statement, the condition will return true.
```c
if(total_cost <= account_balance){
```
Then in the next line, our account balance will be updated by subtracting a negative (or adding a positive) making it large enough to buy the real flag.
```c
account_balance = account_balance - total_cost;
```
Using a sufficiently large number will update the balance, allowing us to buy the real flag from the shop
```
These knockoff Flags cost 900 each, enter desired quantity
999999999

The final cost is: -1943133060

Your current balance after transaction: 1943134160

Welcome to the flag exchange
We sell flags

1. Check Account Balance

2. Buy Flags

3. Exit

 Enter a menu selection
2
Currently for sale
1. Defintely not the flag Flag
2. 1337 Flag
2
1337 flags cost 100000 dollars, and we only have 1 in stock
Enter 1 to buy one1
YOUR FLAG IS: picoCTF{m0n3y_b...}
```
