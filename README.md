# rust-base64
Rust Base 64 implementation

An experiment learning rust.

Base 64 shows binary data on an ASCII format on radix64 format.

V     C    V     C    V     C    Value Char
-----|----|------|----|-----|----|-----|
 0    A    16    Q    32    g    48    w
 1    B    17    R    33    h    49    x
 2    C    18    S    34    i    50    y
 3    D    19    T    35    j    51    z
 4    E    20    U    36    k    52    0
 5    F    21    V    37    l    53    1
 6    G    22    W    38    m    54    2
 7    H    23    X    39    n    55    3
 8    I    24    Y    40    o    56    4
 9    J    25    Z    41    p    57    5
10    K    26    a    42    q    58    6
11    L    27    b    43    r    59    7
12    M    28    c    44    s    60    8
13    N    29    d    45    t    61    9
14    O    30    e    46    u    62    +
15    P    31    f    47    v    63    /


Wikipedia example:

1. Convert content to ASCII number:
	M -> 77 (0x4d)
	a -> 97 (0x61)
	n -> 110 (0x6e)

2. Convert the number (dec or hex) to binary
	M -> 01001101
	a -> 01100001
	n -> 01101110

3. Join the binaries to make one single 24 bits string
	010011010110000101101110

4. Split the string on 6 bits groups
	010011 010110 000101 101110
   
5. Convert each group to decimal
	010011 -> 19
	010110 -> 22
	000101 ->  5
	101110 -> 46

6. Convert each decimal to the equivalence table
	19 -> T
	22 -> W 
	 5 -> F
	46 -> u 

SPECIAL CASES

1. When the number of bytes is not divisible by 3, add zeros at the end to complete the 24 bits.
2. Replace 0 values by = 
	
	M			''			''
	77			0			0
	01001101	00000000	00000000
	010011 010000 000000 000000
	19     16     0      0
	T      Q      =      =


