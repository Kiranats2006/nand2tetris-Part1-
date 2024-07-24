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
![Screenshot 2024-07-23 162824](https://github.com/user-attachments/assets/08406512-f951-4409-a31a-0d49e88d4924)
<img width="959" alt="image" src="https://github.com/user-attachments/assets/dcf80a59-3ce3-4794-aead-1116c2c4487f">
<img width="959" alt="image" src="https://github.com/user-attachments/assets/5d79ec68-f204-4c50-b038-da7670f6c051">
![image](https://github.com/user-attachments/assets/ebf56e7a-5cbc-49b5-8cd2-c8b96599a481)

