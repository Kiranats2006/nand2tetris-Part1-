# nand2tetris-Part1-
HDL CODE:

NOT GATE-

    CHIP Not {
    
    IN in;
    OUT out;

    PARTS:
    Nand(a=in, b=in, out=out);
    }
![Screenshot 2024-07-23 160733](https://github.com/user-attachments/assets/ac07a701-fe68-42a6-a16b-44fc6780cf05)
OR GATE-

    CHIP Or {
    IN a, b;
    OUT out;

    PARTS:
    Nand(a=a, b=a, out=notA);
    Nand(a=b, b=b, out=notB);
    Nand(a=notA, b=notB, out=out);
    }

![Screenshot 2024-07-23 161235](https://github.com/user-attachments/assets/e5ad49fc-5342-4024-9525-fe16a318e28a)

