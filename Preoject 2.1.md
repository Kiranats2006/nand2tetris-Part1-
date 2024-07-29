<img width="960" alt="image" src="https://github.com/user-attachments/assets/aafc96f5-e15a-4204-98ef-98197676caf7">

    CHIP HalfAdder {
    IN a, b;    // 1-bit inputs
    OUT sum,    // Right bit of a + b 
    carry;  // Left bit of a + b
    PARTS:
    And(a=a,b=b,out=carry);
    Xor(a=a,b=b,out=sum);
    }
    
<img width="960" alt="image" src="https://github.com/user-attachments/assets/d365bc60-480d-4eee-9040-9796b5ed9cd9">
    
    CHIP FullAdder {
    IN a, b, c;  // 1-bit inputs
    OUT sum,     // Right bit of a + b + c
    carry;   // Left bit of a + b + c
    PARTS:
    HalfAdder(a=a,b=b,sum=sum1,carry=carry1);
    HalfAdder(a=c,b=sum1,sum=sum,carry=carry2);
    Or(a=carry1,b=carry2,out=carry);
    }
