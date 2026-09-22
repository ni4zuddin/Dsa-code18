#include <stdio.h>
void swap (int *a , int *b){
    int temp = *a;
    *a=*b;
    *b=temp ;
}
int pertition(int array[],int low , int high ){
    int pivot = array[high];
    int i = (low -1 );
    for (int j=low ; j<high ; j++){
        if (array[j]<=pivot){
            i++;
            swap(&array[i],&array[j]);
        }
    }
    swap(&array[i+1],&array[high]);
    return (i+1);
}
void quicksort(int array[],int low , int high){
    if(low<high){
        int pi = pertition(array , low , high );
        quicksort(array , low , pi-1);
        quicksort(array , pi+1, high);
    }
}
void BubbleSort(int arr[], int size) {
    for (int i = 0; i < size - 1; i++) {
        for(int j=0 ; j<size-i-1;j++){
            if (arr[j] > arr[j + 1]) {
                swap(&arr[j],&arr[j+1]);
            }
        }
        break;
    }
    printf("after 1 pass: ");
    for (int i = 0; i < size; i++)
        printf("%d ", arr[i]);
    quicksort(arr, 0, size - 1);
}
int main() {
    int arr[] = {4, 6, 9, 1, 7, 2, 3, 5, 10, 6};
    int size = sizeof(arr) / sizeof(arr[0]);
    BubbleSort(arr, size);
    printf(" sorted array: ");
    for (int i = 0; i < size; i++) {
        printf("%d ", arr[i]);
    }
    return 0;
}
