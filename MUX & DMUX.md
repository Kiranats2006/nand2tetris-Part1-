HDL CODE-

MUX GATE:

    CHIP Mux {
    IN a, b, sel;  // Inputs
    OUT out;       // Output

    PARTS:
    Not(in=sel, out=notsel);
    And(a=a, b=notsel, out=aandnotsel);
    And(a=b, b=sel, out=bandsel);
    Or(a=aandnotsel, b=bandsel, out=out);
    }
  ![Screenshot 2024-07-23 172525](https://github.com/user-attachments/assets/5628b691-9ef5-47bd-a060-531012f0b3cd)

  DMUX GATE:

    CHIP DMux {
    IN in, sel;
    OUT a, b;

    PARTS:
    Not(in=sel, out=notsel);
    And(a=in, b=notsel, out=a);
    And(a=in, b=sel, out=b);
    }

![Screenshot 2024-07-23 172755](https://github.com/user-attachments/assets/237ccd7e-ced7-4c3b-b2a0-f2b5417672b6)

