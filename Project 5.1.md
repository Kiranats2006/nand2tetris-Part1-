    CHIP Memory {
    IN in[16], load, address[15];
    OUT out[16];

    PARTS:
    DMux(in=load, sel=address[14], a=load-ram, b=load-devices);
    DMux(in=load-devices, sel=address[13], a=load-screen);
    RAM16K(in=in, load=load-ram, address=address[0..13], out=ram-out);
    Screen(in=in, load=load-screen, address=address[0..12], out=screen-out);
    Keyboard(out=keyboard-out);
    Mux16(a=screen-out, b=keyboard-out, sel=address[13], out=devices-out);
    Mux16(a=ram-out, b=devices-out, sel=address[14], out=out);
    }

  ![image](https://github.com/user-attachments/assets/43c21c44-71bb-45cb-adf7-88b647483fe5)
