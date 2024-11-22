![image](https://github.com/user-attachments/assets/f6e22abd-dbf4-4f8d-9010-e78476467769)

    CHIP Computer {

    IN reset;

    PARTS:
    ROM32K(address=pc-output, out=program-memory-output);
    CPU(inM=data-memory-output, instruction=program-memory-output, reset=reset, outM=data-memory-input, writeM=write-data-memory, addressM=data-memory-address, pc=pc-output);
    Memory(in=data-memory-input, load=write-data-memory, address=data-memory-address, out=data-memory-output);





    }

