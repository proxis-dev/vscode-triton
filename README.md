<p align="center">
<img width="40%" alt="Screenshot 2024-09-05 at 11 04 21 AM" src="https://github.com/user-attachments/assets/301ff0c8-e0ad-4151-83bf-2b27885b99b4">
</p>

# vscode-triton
This is a vscode extension to convert computationally intensive pytorch kernels to triton.

## The Problem We Faced
ML compilers ( XLA, TorchInductor ) are rule-based emitters to try to codegen efficient kernels. In the past we wrote rules to generate triton kernels for various Gemini models. These were pretty manual and had to be handwritten.

## Where We're Headed
So we thought can we throw out XLA and have o1 generate efficient triton kernels instead?

1: o1 reads code and extracts computationally heavy kernels ( GEMM, RMS norm, etc )
2: o1 rewrites pytorch code in triton, for ~100x speedups

RMS norm (used in modern LLMs) are row-wise independent, we can use triton to force each row to execute independently on difference threads.

## The Numbers: 8.5s down to 0.05s
<img width="800" alt="image" src="https://github.com/user-attachments/assets/a8fd929c-4708-4b91-b6a2-152d8a64faf5">

## Get In Touch
Let us know if you find the same success as we did with these tools.

Come hang with us on Discord [here](https://discord.gg/fHuVCMtT).



