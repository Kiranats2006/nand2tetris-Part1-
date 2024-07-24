HDL CODE-

AND GATE:
  
    CHIP And {
    IN a, b;
    OUT out;
    
    PARTS:
    Nand(a=a,b=b,out=nandOut);
    Nand(a=nandOut,b=nandOut,out=out);
    }
![Screenshot 2024-07-23 162824](https://github.com/user-attachments/assets/559856c9-b14e-4f6d-be38-5e73775465a3)
XOR GATE:

    CHIP Xor {
    IN a, b;
    OUT out;

    PARTS:
        Nand(a=a, b=b, out=nand1);       
    Nand(a=a, b=nand1, out=nand2);    
    Nand(a=b, b=nand1, out=nand3);    
    Nand(a=nand2, b=nand3, out=out);
    }
 ![Screenshot 2024-07-23 163459](https://github.com/user-attachments/assets/4a8ed45c-7b11-483e-ad9a-062a0d76e566)
