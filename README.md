Download Link: https://assignmentchef.com/product/solved-cs2208b-lab-no-5
<br>
<h1>Bubble sort algorithm</h1>

The bubble sort is a simple sorting algorithm that repeatedly steps through the list to be sorted, compares each pair of adjacent items and swaps them if they are in the wrong order. The pass through the list is repeated until no swaps are needed, which indicates that the list is sorted. The algorithm, which is a comparison sort, is named for the way smaller elements <strong><em>bubble</em></strong> to the top of the list. This flowchart describes the algorithm. Below, is an implementation for this flowchart using C.

<strong>int main() </strong>

<strong>{ </strong>

<strong>    int a[]={44, -56, 300, 65, -8, 32, 6, -87,  </strong>

<strong>             54,  65,  87, 32, 65};     int n, i, j;</strong>

<strong> </strong>

<strong>    n = sizeof(a)/sizeof(a[0]);     for (i = 0; i &lt; n-1; i++)</strong> <strong>    { for (j = 0; j &lt; n-1-i; j++)</strong> <strong>        sortTwo(&amp;a[j], &amp;a[j+1]);</strong>

<strong>    }</strong> <strong>    return 0; </strong>

<strong>}</strong>




In ARM assembly, you can convert the algorithm as follows:

<strong>main       ADR r0,a  ;r0 is a pointer to array a </strong>

<strong>           ADR r1,endOfArray ;address at the end of the array </strong>

<strong>           SUB r1,r1,r0      ;number of the array bytes </strong>

<strong>           ASR r1,#2         ;r1: length of the array,i.e., n </strong>

<strong> </strong>

<strong>           MOV r2,#0         ;r2: outer loop counter,i.e., i </strong>

<strong>           SUB r4,r1,#1      ;r4 is (n – 1) </strong>

<strong>startOuter CMP r2,r4         ;compare i with (n – 1)  </strong>

<strong>           BGE endOuter      ;if i &gt;= (n – 1), then exit the outer loop </strong>

<strong>           MOV r3,#0         ;r3 is the inner loop counter, i.e., j </strong>

<strong>           SUB r5,r4,r2      ;r5 is (n – 1 – i) </strong>

<strong>startInner CMP r3,r5         ;compare j with (n – 1 – j)  </strong>

<strong>           BGE endInner      ;if j &gt;= (n – 1 -j), then exit the inner loop </strong>

<strong>           ADD r6,r0,r3,LSL#2;r6 is a pointer to a[j] </strong>

<strong>           ADD r7,r6,#4      ;r7 is a pointer to a[j+1] </strong>

<strong>           BL  sortTwo       ;call sortTwo(*a[j],*a[j+1]) </strong>

<strong>      ADD r3,r3,#1      ;increment inner counter j    B   startInner    ;loop again (inner loop) endInner ADD r2,r2,#1      ;increment outer counter i         B   startOuter    ;loop again (outer loop) endOuter B endOuter </strong>

<strong> </strong>

<strong>a          DCD 44,-56,3,65,-8,32,6,-87,54,65,87,32,65 endOfArray SPACE 1 </strong>

Copyright © 2016 Mahmoud El-Sakka.




<h1>PROBLEM SET</h1>

Before you start practicing this lab, you need to review and fully understand how to use <em>the Keil ARM Simulator</em>, as well as tutorial 8<em> (Tutorial_08_ARM_Subroutine_Call_and_Return.pdf).</em>

<strong> </strong>

<ol>

 <li>Fully understand the two codes above.</li>

 <li>Implement the <strong>sortTwo</strong> The function must not alter any register value. If you want to use any, you have to store the original value in the stack before changing them and you have to retrieve the original value before returning from the function.</li>

 <li>Change the <strong>main</strong> and the <strong>sortTwo</strong> functions in such a way that you utilize the stack when calling the <strong>sortTwo</strong> function, i.e., do <strong><em><u>not</u></em></strong> utilize the <strong>LR</strong>.</li>

 <li>Change the main in such a way that if no change occurs inside the inner loop for one full cycle, then you exit the outer loop, as the list will be already sorted in such a situation.</li>

</ol>

Copyright © 2016 Mahmoud El-Sakka.