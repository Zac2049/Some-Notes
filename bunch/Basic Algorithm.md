# Basic Algorithm924312430

## 考研部分

1. 折半查找

   ```c++
   int BinarySearch(SeqList L , ElemType key){
       int low = 0, high = L.TableLen -1 , mid;
       while( low <= high ){
           mid = ( low + high )/2;
           if(L.elem[mid] == key)
               return mid;
           else if(L.elem[mid] > key)
               high = mid - 1;
           else 
               low = mid + 1;
       }
       return -1;
   }
   ```

2. 插入排序

   ```c++
   void InsertSort(ElemType A[] , int n){
       int i , j;
       for(i = 2; i <= n; i++)
           if(A[i] < A[i-1]){
               A[0] = A[i];
               for(j = i-1 ; A[0] < A[j] ; --j)
                   A[j+1] = A[j];
               A[j+1] = A[0];
           }
   }
   //折半插入
   void InsertSort(ElemType A[] , int n){
       int i,j,low,high,mid;
       for(i = 2; i <= n; i++){
           A[0] = A[i];
           low = 1 ; high = i-1;
           while(low <= high){
               mid = (low + high)/2;
               if(A[mid] > A[0])high = mid - 1;
               else low = mid + 1;
           }
           for(j = i-1 ; j >= high+1 ; --j)
               A[j+1] = A[j];
           A[high+1] = A[0];
       }
   }
   //Shell排序
   void ShellSort(ElemType A[] , int n){
       for(dk = n/2 ; dk > =1 ; dk = dk/2)
           for(i = dk+1 ; i <= n ; ++i)
               if(A[i] < A[i-dk]){
                   A[0] = A[i];
                   for(j = i-dk ; j>0 && A[0]<A[j] ; j-=dk)
                       A[j+dk] = A[j];
                   A[j+dk] = A[0];
               }
   }
   ```

3. 交换排序

   ```c++
   //冒泡排序
   void BubbleSort(ElemType A[] , int n){
       for(i = 0 ; i < n-1 ; i++){
           flag = false;
           for(j = n-1 ; j > i ; j--)
               if(A[j-1] > A[j]){
                   swap(A[j-1] , A[j]);
                   flag = true;
               }
           if(flag == false)
               return;
       }
   }
   //快速排序
   int Partition(ElemType A[] , int low , int high){
       ElemType pivot = A[low];
       while(low < high){
           while(low<high && A[high] >= pivot)--high;
           A[low] = A[high];
           while(low<high && A[low] <= pivot)++low;
           A[high] = A[low];
       }
       A[low] = pivot;
       return low;
   }
   void QuickSort(ElemType A[] , int low , int high){
       if(low < high){
           int pivotpos = Partition(A , low , high);
           QuickSort(A , low , pivotpos-1);
           QuickSort(A , pivotpos+1 , high);
       }
   }
   ```

4. 选择排序

   ```c++
   //简单选择
   void SelectSort(ElemType A[] , int n){
       for(int i = 0 ; i < n-1 ; i++){
           min = i;
           for(j= i+1 ; j < n ; j++)
               if(A[j] < A[min])min = j;
           if(min != j)swap(A[i] , A[min]);
       }
   }
   //堆排序
   //建立大根堆
   void BuildMaxHeap(ElemType A[] , int low){
       for(int i = len/2 ; i > 0 ; i--)
           HeadAdjust(A , i , low);
   }
   void HeadAdjust(ElemType A[] , int k ; int len){
       A[0] = A[k];
       for(i = 2*k ; i <= len ; i*=2){
           if(i<len && A[i]<A[i+1])
               i++;
           if(A[0] >= A[i])break;
           else{
               A[k] = A[i];
               k = i;
           }
       }
       A[k] = A[0];
   }
   //堆排序
   void HeapSort(ElemType A[] , int len){
       BuildMaxHeap(A , len);
       for(i = len ; i > 1 ; i--){
           swap(A[i] , A[1]);
           HeadAdjust(A , 1 , i-1);
       }
   }
   ```

5. 归并排序

   ```c++
   ElemType* B = new ElemType[n+1];
   void Merge(ElemType A[] , int len , int mid , int high){
       for(int k = low ; k <= high ; k++)
           B[k] = A[k];//先复制
       for(i=low , j=mid+1 , k=i ; i<=mid && j<=high ; k++){
           if(B[i] <= B[j])A[k] = B[i++];//再粘贴
           else A[k] = B[j++];
       }
       while(i <= mid)A[k++] = B[i++];
       while(i <= high)A[k++] = B[j++];//本质问题，两个已递增序列合并为一个递增序列，三指针
   }
   void MergeSort(ElemType A[] , int low , int high){
       if(low < high){
           int mid = (low + high)/2;
           MergeSort(A , low , mid);
           MergeSort(A , mid+1 , high);
           Merge(A , low , mid , high);
       }
   }
   ```

   

