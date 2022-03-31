import numpy as np
import ctypes
### 将32位数差分成4个8位数
def convert(int32_val):
    bin = np.binary_repr(int32_val, width = 32) 
    int8_arr = [int(bin[0:8],2), int(bin[8:16],2), 
                int(bin[16:24],2), int(bin[24:32],2)]
    return int8_arr


### 将4个8位合成一个32位
def convert(a):
    num = ctypes.int8(a[0]).value << 24 | a[1] << 16 | a[2] << 8 | a[3]
    return num
