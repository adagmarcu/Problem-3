// Problem-3

#include <iostream>
#include <string.h>
#include <stdlib.h>
#include <bits/stdc++.h>
using namespace std;

list<char> minimalLexicographicallyString(list<char> firstList, list<char> secondList) {

    list<char> result;
    list<char>::iterator it;
    while (firstList.size() > 0 || secondList.size() > 0)
    {
        if (firstList.size() == 0) {
            for (it = secondList.begin(); it != secondList.end(); it++)
            {
                result.push_back(*it);
            }
            secondList.clear();
        }
        else if (secondList.size() == 0) {
            for (it = firstList.begin(); it != firstList.end(); it++)
            {
                result.push_back(*it);
            }
            firstList.clear();
        }
        else {
            char firstLetterFirstList = firstList.front();
            char firstLetterSecondList = secondList.front();
            char* pChar1 = &firstLetterFirstList;
            char* pChar2 = &firstLetterSecondList;
            if (strcmp(pChar1, pChar2) <= 0) {
                result.push_back(firstLetterFirstList);
                firstList.pop_front();
            }
            else {
                result.push_back(firstLetterSecondList);
                secondList.pop_front();
            }
        }
    }
    return result;
}

int main()
{
    list<char>::iterator it;
    list<char> list1, list2, list3;
    list1.push_back('a');
    list1.push_back('c');
    list1.push_back('a');
    list2.push_back('b');
    list2.push_back('c');
    list2.push_back('f');
    list3 = minimalLexicographicallyString(list1, list2);
    for (it = list3.begin(); it != list3.end(); it++)
    {
        cout << *it;
    }
}
