# -2-
2分搜尋(記事本)
#include <stdio.h>

#define MAX_SIZE 100000

int binarysearch(int a[], int findnumber, int left, int right);

int main() {
    int arr[MAX_SIZE];
    int n = 0;
    FILE *file = fopen("bss.txt", "r");
    if (file == NULL) {
        printf("Unable to open file.\n");
        return 1;
    }

    // ?文件中?取?据并存入??
    while (fscanf(file, "%d", &arr[n]) != EOF && n < MAX_SIZE) {
        n++;
    }

    fclose(file);

    // 二分搜索需要??是有序的，?里假??据已?有序
    // 如果?据?有排序，?在此?添加排序算法

    int findnumber = 45;
    int result = binarysearch(arr, findnumber, 0, n - 1);
    if (result == -1) {
        printf("Element %d not found\n", findnumber);
    } else {
        printf("Element %d found at index %d\n", findnumber, result);
    }

    return 0;
}

int binarysearch(int a[], int findnumber, int left, int right) {
    int middle; // 中

    middle = (left + right) / 2;

    if (left > right) {
        return -1;
    }

    if (a[middle] == findnumber) {
        return middle;
    }

    if (a[middle] > findnumber) {
        return binarysearch(a, findnumber, left, middle - 1);
    } else {
        return binarysearch(a, findnumber, middle + 1, right);
    }
}























