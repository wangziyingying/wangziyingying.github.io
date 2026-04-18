# week1

****

**Puzzle**

  下载之后使用exe打开，发现无壳，是64位。用ida64打开。

![](C:\Users\22382\OneDrive\图片\Screenshots\屏幕截图 2026-04-15 190742.png)

F5进入main函数。

![](C:\Users\22382\OneDrive\图片\Screenshots\屏幕截图 2026-04-15 190802.png)

发现flag是由四部分组成。点进puzzle_challenge函数，发现这部分flag是由Destination和v2组成，part1:Do_YOu_

![](C:\Users\22382\OneDrive\图片\Screenshots\屏幕截图 2026-04-15 191558.png)

返回上一个页面，接着点进puts-buffer，发现part4:1e_Gam3，往下看到second part是part2:Like_7his_Jig 。

![](C:\Users\22382\OneDrive\图片\Screenshots\屏幕截图 2026-04-15 192741.png)

返回到最初页面，看到左边的Its_about_part3，是part3

![](C:\Users\22382\OneDrive\图片\Screenshots\屏幕截图 2026-04-16 190910.png)

点进去发现是异或

![](C:\Users\22382\OneDrive\图片\Screenshots\屏幕截图 2026-04-16 192020.png)

点进encrypted_arry，按shift和e找到encrypted_arry的值

![](C:\Users\22382\OneDrive\图片\Screenshots\屏幕截图 2026-04-16 191957.png)

运行这个程序，得出part3：s@w_puzz

\#include <stdio.h>

 int main() {  

 unsigned char arr[] = {0xDE,0xED,0xDA,0xF2,0xDD,0xD8,0xD7,0xD7};              int i, len = sizeof(arr)/sizeof(arr[0]);   

  for(i=0; i<len; i++){  

​      printf("0x%02X ^ 0xAD = 0x%02X  -> %c\n", arr[i], arr[i]^0xAD,

arr[i]^0xAD);    }    

 return 0;

 }

所以flag{Do_Y0u_Like_7his_Jigs@w_puzz1e_Gam3}

##### Strang Base

64位无壳

F5

![](C:\Users\22382\OneDrive\图片\Screenshots\屏幕截图 2026-04-15 202929.png)

进入puts

![](C:\Users\22382\OneDrive\图片\Screenshots\屏幕截图 2026-04-16 205002.png)

看HELlo!A=CrQzy-B453|is

shift+e![](C:\Users\22382\OneDrive\图片\Screenshots\屏幕截图 2026-04-16 204952.png)



用cyberchef解出![](C:\Users\22382\OneDrive\图片\Screenshots\屏幕截图 2026-04-16 204918.png)

得到flag{Wh4t_a_cra2y_8as3!!!}

##### xor

64位，用ida打开

![](C:\Users\22382\OneDrive\图片\Screenshots\屏幕截图 2026-04-17 200023.png)

是一个异或加密

运行程序

#include<bits/stdc++.h>
using namespace std;
char s[26]={"anu`ym7wKLl$P]v3q%D]lHpi"};  
int v5[3]; 
signed main(){
    for (int i=0;i<24;++i){
    	if ( i % 3 ){
            if ( i % 3 == 1 ) s[i] ^= 0x11u;
            else s[i] ^= 0x45u;
        }
      else s[i] ^= 0x14u;
	} 
    v5[0] = 19;
    v5[1] = 19;
    v5[2] = 81;	 
    for (int i=0;i<24;++i) {
    	s[i]^=v5[i%3];
		cout<<s[i]; 
	} 
	return 0;
} 

得到flag{y0u_Kn0W_b4s1C_xOr}
