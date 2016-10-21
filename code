#include<stdio.h>
#include<stdlib.h>
#include<time.h>

#define max 100000000


int main() {
	clock_t begin, end;
	begin = clock();
	unsigned long count = 0;
	unsigned long i, j;
	char *a;//若直接使用数组进行计算会产生栈溢出的错误，这是因为定义数组的大小是有限制的，超过这个范围则会报错
	a = (char *)malloc(max*sizeof(char));//在debug模式下调用的free时会报堆错误，因为a所指的地址发生了改变，导致无法正常free。而在release下可正常运行
	for (i = 0; i <= max; i++)
		a[i] = 1;
	for (i = 2; i*i < max; i++) {
		if (a[i] == 0)
			continue;
		for (j = i*i; j <= max; j+=i) {//按倍数i往上加，直接删除i的倍数，不用再一个个循环。
			/*if (j / i != 1 && j%i == 0)//因为i的平方以内也不会有偶数所以应从i的平方开始
				a[j] = 0;*/
			a[j] = 0;
		}
	}
	for (i = 2; i <= max; i++)
		if (a[i] != 0)
			count++;
	end = clock();
	//free(a);
	printf("count=%ld\n %f\n",count, (double)(end - begin) / CLOCKS_PER_SEC);
	return 0;
}
