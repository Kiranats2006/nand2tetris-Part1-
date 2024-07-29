<img width="960" alt="image" src="https://github.com/user-attachments/assets/aafc96f5-e15a-4204-98ef-98197676caf7">

    CHIP HalfAdder {
    IN a, b;    // 1-bit inputs
    OUT sum,    // Right bit of a + b 
    carry;  // Left bit of a + b
    PARTS:
    And(a=a,b=b,out=carry);
    Xor(a=a,b=b,out=sum);
    }
