BIT 
    
    CHIP Bit {
    IN in, load;
    OUT out;

    PARTS:
       Mux(a=dout,b=in,sel=load,out=out1);
    DFF(in=out1,out=dout,out=out);
    }


![image](https://github.com/user-attachments/assets/7d95ce86-814c-4648-b93f-eb5bd520dfee)

REGISTER

    CHIP Register {
    IN in[16], load;
    OUT out[16];

    PARTS:
    Bit(in=in[0],load=load,out=out[0]);
    Bit(in=in[1],load=load,out=out[1]);
    Bit(in=in[2],load=load,out=out[2]);
    Bit(in=in[3],load=load,out=out[3]);
    Bit(in=in[4],load=load,out=out[4]);
    Bit(in=in[5],load=load,out=out[5]);
    Bit(in=in[6],load=load,out=out[6]);
    Bit(in=in[7],load=load,out=out[7]);
    Bit(in=in[8],load=load,out=out[8]);
    Bit(in=in[9],load=load,out=out[9]);
    Bit(in=in[10],load=load,out=out[10]);
    Bit(in=in[11],load=load,out=out[11]);
    Bit(in=in[12],load=load,out=out[12]);
    Bit(in=in[13],load=load,out=out[13]);
    Bit(in=in[14],load=load,out=out[14]);
    Bit(in=in[15],load=load,out=out[15]);
    }

![image](https://github.com/user-attachments/assets/24e1427f-706e-4d7b-8eac-66b658f62ee1)

RAM8

    CHIP RAM8 {
    IN in[16], load, address[3];
    OUT out[16];

    PARTS:
    DMux8Way(in=load,sel=address,a=load0,b=load1,c=load2,d=load3,e=load4,f=load5,g=load6,h=load7);
    Register(in=in,load=load0,out=out0);
    Register(in=in,load=load1,out=out1);
    Register(in=in,load=load2,out=out2);
    Register(in=in,load=load3,out=out3);
    Register(in=in,load=load4,out=out4);
    Register(in=in,load=load5,out=out5);
    Register(in=in,load=load6,out=out6);
    Register(in=in,load=load7,out=out7);
    Mux8Way16(a=out0,b=out1,c=out2,d=out3,e=out4,f=out5,g=out6,h=out7,sel=address,out=out);
    }
![image](https://github.com/user-attachments/assets/02856ede-11ec-43b7-916d-7fe49523adc8)

RAM64

    CHIP RAM64 {
    IN in[16], load, address[6];
    OUT out[16];

    PARTS:
    DMux8Way(in=load,sel=address[3..5],a=load0,b=load1,c=load2,d=load3,e=load4,f=load5,g=load6,h=load7);
    RAM8(in=in,load=load0,address=address[0..2],out=out0);
    RAM8(in=in,load=load1,address=address[0..2],out=out1);
    RAM8(in=in,load=load2,address=address[0..2],out=out2);
    RAM8(in=in,load=load3,address=address[0..2],out=out3);
    RAM8(in=in,load=load4,address=address[0..2],out=out4);
    RAM8(in=in,load=load5,address=address[0..2],out=out5);
    RAM8(in=in,load=load6,address=address[0..2],out=out6);
    RAM8(in=in,load=load7,address=address[0..2],out=out7);
    Mux8Way16(a=out0,b=out1,c=out2,d=out3,e=out4,f=out5,g=out6,h=out7,sel=address[3..5],out=out);}
![image](https://github.com/user-attachments/assets/a92b2fd9-1dc1-4cbf-9e99-50226b1075dd)





    

