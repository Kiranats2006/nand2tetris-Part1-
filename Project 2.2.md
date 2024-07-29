<img width="960" alt="image" src="https://github.com/user-attachments/assets/ff0d009b-dd77-4a62-9731-1c50fbe3a257">

    CHIP Add16 {
    IN a[16], b[16];
    OUT out[16];

    PARTS:
    HalfAdder(a=a[0],b=b[0],sum=out[0],carry=carry1);
  	FullAdder(a=a[1],b=b[1],c=carry1,sum=out[1],carry=carry2);
  	FullAdder(a=a[2],b=b[2],c=carry2,sum=out[2],carry=carry3);
  	FullAdder(a=a[3],b=b[3],c=carry3,sum=out[3],carry=carry4);
  	FullAdder(a=a[4],b=b[4],c=carry4,sum=out[4],carry=carry5);
  	FullAdder(a=a[5],b=b[5],c=carry5,sum=out[5],carry=carry6);
  	FullAdder(a=a[6],b=b[6],c=carry6,sum=out[6],carry=carry7);
  	FullAdder(a=a[7],b=b[7],c=carry7,sum=out[7],carry=carry8);
  	FullAdder(a=a[8],b=b[8],c=carry8,sum=out[8],carry=carry9);
  	FullAdder(a=a[9],b=b[9],c=carry9,sum=out[9],carry=carry10);
  	FullAdder(a=a[10],b=b[10],c=carry10,sum=out[10],carry=carry11);
  	FullAdder(a=a[11],b=b[11],c=carry11,sum=out[11],carry=carry12);
  	FullAdder(a=a[12],b=b[12],c=carry12,sum=out[12],carry=carry13);
  	FullAdder(a=a[13],b=b[13],c=carry13,sum=out[13],carry=carry14);
  	FullAdder(a=a[14],b=b[14],c=carry14,sum=out[14],carry=carry15);
  	FullAdder(a=a[15],b=b[15],c=carry15,sum=out[15],carry=carry16);
    }

  <img width="960" alt="image" src="https://github.com/user-attachments/assets/4dc9627f-8af6-4661-94d8-21f11034f9ce">

    CHIP Inc16 {
    IN in[16];
    OUT out[16];

    PARTS:
    Add16(a=in,b[0]=true,b[1..15]=false,out=out);
    }
<img width="960" alt="image" src="https://github.com/user-attachments/assets/2f0aef58-0607-4036-a851-2e3804627ede">


    CHIP ALU {
    IN  
        x[16], y[16],  // 16-bit inputs        
        zx, // zero the x input?
        nx, // negate the x input?
        zy, // zero the y input?
        ny, // negate the y input?
        f,  // compute (out = x + y) or (out = x & y)?
        no; // negate the out output?
    OUT 
        out[16], // 16-bit output
        zr,      // if (out == 0) equals 1, else 0
        ng;      // if (out < 0)  equals 1, else 0

    PARTS:
        // if (zx==1) set x = 0
    Mux16(a=x,b=false,sel=zx,out=zxout);

    // if (zy==1) set y = 0
    Mux16(a=y,b=false,sel=zy,out=zyout); 

    // if (nx==1) set x = ~x
    // if (ny==1) set y = ~y  
    Not16(in=zxout,out=notx);
    Not16(in=zyout,out=noty);
    Mux16(a=zxout,b=notx,sel=nx,out=nxout); 
    Mux16(a=zyout,b=noty,sel=ny,out=nyout);

    // if (f==1)  set out = x + y 
    // if (f==0)  set out = x & y
    Add16(a=nxout,b=nyout,out=addout);
    And16(a=nxout,b=nyout,out=andout);
    Mux16(a=andout,b=addout,sel=f,out=fout);
    
    // if (no==1) set out = ~out
    // 1 if (out<0),  0 otherwise
    Not16(in=fout,out=nfout);
    Mux16(a=fout,b=nfout,sel=no,out=out,out[0..7]=zr1,out[8..15]=zr2,out[15]=ng);
    
    // 1 if (out==0), 0 otherwise
    Or8Way(in=zr1,out=or1);
    Or8Way(in=zr2,out=or2);
    Or(a=or1,b=or2,out=or3);
    Not(in=or3,out=zr);
}

