### Kernel Components:

1. **Pipeline**: Contains kernel arguments and the computation logic. It defines how the data will move and what computation will happen within the kernel. It’s essentially the core of the kernel.
    
2. **Epilogue**: Defines the post-processing of the kernel’s results. Once the kernel computation is done, the epilogue handles actions like reshuffling the output data to the desired format (e.g., converting results into row format) or applying activation functions like adding constants.
    

### Pipeline Subdivisions:

1. **Problem**: Describes the parameters needed to define the kernel (e.g., tensor dimensions, strides, etc.).
    
2. **Tile Pipeline**: Defines what each "tile" (a smaller chunk of data) does during execution. You can either define your own tile pipeline or reuse existing ones provided by CK authors.
    
3. **Policy**: Defines the optimization strategies at the tile level (e.g., padding techniques that don’t change the tensor’s memory layout). Like tile pipelines, you can define your own optimizations or reuse existing ones.
    

### Example: GEMM (General Matrix Multiply)

In the case of GEMM, the terms pipeline, epilogue, policy, and tile pipeline are used because they compose the kernel. However, the specific implementation details of these components are unclear to your coworker, especially how they are defined and how data is scheduled on hardware based on memory-bound or compute-bound operations.

### Types of Pipelines in CK:

1. **Memory Pipeline**: Used for memory-bound operations.
2. **ComputeV3 Pipeline**: Used for compute-bound operations.
3. **ComputeV4 Pipeline**: A "ping-pong" pipeline that is currently being worked on (possibly by Sudhir).

### Epilogue (as described by Thomas):

The epilogue handles the final stage of the computation, where the results in registers or cache are stored back into memory, often requiring shuffling to match a desired format (e.g., row format). The example mentioned is the **CShuffle** operation in older CK versions.

Block -> Wavefront-> Thread
Block Tile -> WaveTile ->Vectors
