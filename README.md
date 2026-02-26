# c-1
Ex00 — ft_putchar.c
#include <unistd.h>

void ft_putchar(char c)
{
    write(1, &c, 1);
}



Ex01 — ft_print_alphabet.c

#include <unistd.h>

void ft_print_alphabet(void)
{
    char c = 'a';
    while (c <= 'z')
        write(1, &c++, 1);
}

Ex02 — ft_print_reverse_alphabet.c

#include <unistd.h>

void ft_print_reverse_alphabet(void)
{
    char c = 'z';
    while (c >= 'a')
        write(1, &c--, 1);
}


Ex03 — ft_print_numbers.c
#include <unistd.h>

void ft_print_numbers(void)
{
    char c = '0';
    while (c <= '9')
        write(1, &c++, 1);
}


Ex04 — ft_is_negative.c
#include <unistd.h>

void ft_is_negative(int n)
{
    if (n < 0)
        write(1, "N", 1);
    else
        write(1, "P", 1);
}

Ex05 — ft_print_comb.c

#include <unistd.h>

void ft_print_comb(void)
{
    char a, b, c;

    a = '0';
    while (a <= '7')
    {
        b = a + 1;
        while (b <= '8')
        {
            c = b + 1;
            while (c <= '9')
            {
                write(1, &a, 1);
                write(1, &b, 1);
                write(1, &c, 1);
                if (!(a == '7' && b == '8' && c == '9'))
                    write(1, ", ", 2);
                c++;
            }
            b++;
        }
        a++;
    }
}


Ex06 — ft_print_comb2.c
#include <unistd.h>

void ft_print_comb2(void)
{
    int a = 0;
    while (a <= 98)
    {
        int b = a + 1;
        while (b <= 99)
        {
            char out[5];
            out[0] = '0' + a / 10;
            out[1] = '0' + a % 10;
            out[2] = ' ';
            out[3] = '0' + b / 10;
            out[4] = '0' + b % 10;
            write(1, out, 5);
            if (!(a == 98 && b == 99))
                write(1, ", ", 2);
            b++;
        }
        a++;
    }
}

Ex07 — ft_putnbr.c

#include <unistd.h>

void ft_putnbr(int nb)
{
    if (nb == -2147483648)
    {
        write(1, "-2147483648", 11);
        return;
    }
    if (nb < 0)
    {
        write(1, "-", 1);
        nb = -nb;
    }
    if (nb >= 10)
        ft_putnbr(nb / 10);
    char c = '0' + (nb % 10);
    write(1, &c, 1);
}

Ex08 — ft_print_combn.c
#include <unistd.h>

void print_comb(char *arr, int n)
{
    int i = 0;
    while (i < n)
        write(1, &arr[i++], 1);
    write(1, ", ", 2);
}

void ft_print_combn(int n)
{
    char arr[10];
    for (int i = 0; i < n; i++)
        arr[i] = i + '0';

    while (arr[0] <= '9' - n + 1)
    {
        print_comb(arr, n);

        int pos = n - 1;
        while (pos >= 0 && arr[pos] == '9' - (n - 1 - pos))
            pos--;
        if (pos < 0) break;
        arr[pos]++;
        for (int j = pos + 1; j < n; j++)
            arr[j] = arr[j - 1] + 1;
    }
}

