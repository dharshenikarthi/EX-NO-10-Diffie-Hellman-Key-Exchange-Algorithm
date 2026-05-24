# EX-NO-10-Diffie-Hellman-Key-Exchange-Algorithm

## AIM:
To Implement Diffie Hellman Key Exchange Algorithm 

## Algorithm:

1. Diffie-Hellman Key Exchange is used for securely sharing a secret key between two parties over an insecure channel.

2. Initialization: Agree on a large prime number \( p \) and a primitive root \( g \) modulo \( p \) (both are public values).

3. Key Exchange Process: 
   - Each party selects a private key and calculates their public key using the formula \( g^{\text{private key}} \mod p \).
   - Each party then shares their public key with the other.

4. Secret Key Computation: 
   - Each party computes the shared secret key using the received public key and their own private key.

5. Security: The difficulty of computing discrete logarithms ensures that the shared key remains secure even if public values are intercepted.

## Program:
```
#include <stdio.h>

long long power(long long a, long long b, long long mod)
{
    long long result = 1;
    while(b > 0)
    {
        if(b % 2 == 1)
        {
            result = (result * a) % mod;
        }
        a = (a * a) % mod;
        b = b / 2;
    }
    return result;
}

int main()
{
    long long p, g, a, b;

    printf("DIFFIE HELLMAN KEY EXCHANGE\n");

    printf("\nEnter Prime Number (p): ");
    scanf("%lld", &p);

    printf("Enter Primitive Root (g): ");
    scanf("%lld", &g);

    printf("Enter Private Key of User 1: ");
    scanf("%lld", &a);

    printf("Enter Private Key of User 2: ");
    scanf("%lld", &b);

    long long A = power(g, a, p);
    long long B = power(g, b, p);

    long long key1 = power(B, a, p);
    long long key2 = power(A, b, p);

    printf("\nPublic Value p = %lld", p);
    printf("\nPublic Value g = %lld", g);

    printf("\n\nPrivate Key User 1 = %lld", a);
    printf("\nPrivate Key User 2 = %lld", b);

    printf("\n\nPublic Key User 1 = %lld", A);
    printf("\nPublic Key User 2 = %lld", B);

    printf("\n\nShared Secret Key User 1 = %lld", key1);
    printf("\nShared Secret Key User 2 = %lld", key2);

    if(key1 == key2)
    {
        printf("\n\nKey Exchange Successful");
    }
    else
    {
        printf("\n\nKey Exchange Failed");
    }

    return 0;
}
```


## Output:

<img width="1615" height="839" alt="image" src="https://github.com/user-attachments/assets/05f4cc77-6281-4a2e-aa89-bf11dab40824" />


## Result:
  The program is executed successfully

