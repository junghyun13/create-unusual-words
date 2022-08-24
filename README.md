# create-unusual-words
# Return a string in which the first character is the even-numbered alphabet by its 0th index, and the even-numbered letter of each word is capitalized and the odd-numbered letter is converted to lowercase (however, spaces must also be counted as numbers)! 첫 번째 글자는 0번째 인덱스로 보아 짝수번째 알파벳이고  각 단어의 짝수번째 알파벳은 대문자로, 홀수번째 알파벳은 소문자로 바꾼 문자열을 리턴해라(단, 공백도 숫자로 세야함)!
# c program
# case 1:
#include <stdio.h>
#include <stdbool.h>
#include <stdlib.h>
#include <ctype.h>
#include <string.h>
char* solution(const char* s) {
    char* answer = (char*)malloc(1 * strlen(s) + 1); // 짝수번째 +1 은 NULL 문자 까지 
    strcpy(answer, s); 
    bool isodd = true; //bool type 을 선언하여 짝수인덱스인지를 판별
    for(int i = 0; i <strlen(s); i++)
    {
        if(answer[i] == ' ')  { //answer[i] 의 띄어쓰기 가 들어온다면 if 실행
            isodd = true;
            continue; // continue 를 사용하여 탈출
        }
        if(isodd) // bool type isodd 가 참 이라면 
            answer[i] = toupper(answer[i]);
        else
            answer[i] = tolower(answer[i]);
        isodd = !isodd;
        }
    return answer;}
int main(void){
    char s;
    char* solution(const char* s);
    s='try hello world';
    solution(s);
    return 0;
}
# case 2:
#include <stdio.h>
#include <stdbool.h>
#include <stdlib.h>

// 파라미터로 주어지는 문자열은 const로 주어집니다. 변경하려면 문자열을 복사해서 사용하세요.
char* solution(const char* s) {
    // return 값은 malloc 등 동적 할당을 사용해주세요. 할당 길이는 상황에 맞게 변경해주세요.
    //대문자 65~90
    //소문자 97~122
    int len;
    int i;
    char* answer = (char*)malloc(100000000);
    bool capital = true;
    while(s[len]) len++;
    for(i=0; i<len; i++){
        if(s[i] == ' '){
            answer[i] = s[i];
            capital = true;
            continue;
        } 
        if(capital)
            answer[i] = (s[i] >= 65 && s[i] <= 90) ? s[i] : s[i] - 32;
        else
            answer[i] = (s[i] >= 97 && s[i] <= 122) ? s[i] : s[i] + 32;
        capital = capital^1;
    }       
    return answer;}
#result--> "TrY HeLlO WoRlD"
