快手网红爆料网站大全快手爆料今日大赛今日


5 流回调

流回调是一种特别的技术，有点像是事件的函数，这个回调函数被放入流中，当其前面的任务都完成了，就会调用这个函数，但是比较特殊的是，在回调函数中，需要遵守下面的规则

    回调函数中不可以调用CUDA的API
    不可以执行同步

流函数有特殊的参数规格，必须写成下面形式参数的函数;

void CUDART_CB my_callback(cudaStream_t stream, cudaError_t status, void *data) {
    printf("callback from stream %d\n", *((int *)data));
}

然后使用：

cudaError_t cudaStreamAddCallback(cudaStream_t stream,cudaStreamCallback_t callback, void *userData, unsigned int flags);

#include <cuda_runtime.h>
