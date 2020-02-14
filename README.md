.model tiny
.386
.data
dat1 db 01H,05H,11H,66H,07H
dat2 db 41H,87H,00H,31H,70H

.code
.startup
LEA SI,DAT1
LEA DI,DAT2
MOV AX,0000H
MOV BL,00H
MOV CL,05H
CLC
X1:  	MOV AL,[SI]
        ADC AL,[DI]
        MOV [DI+20],AL
        INC SI 
        INC DI
        DEC CL
        JNZ X1
        JNC X2
        INC BL
X2:  MOV [DI+20],BL
.exit
end

//2

.model tiny
.386
.data

array1 db 50 dup(22H)
abc db    10 dup(?)
array2 db 50 dup(11H)

.code
.startup

LEA SI, array1
LEA DI,array2
MOV AX,0000H
MOV CL,32H

  X1:    	MOV AL,[SI]
            MOV [DI],AL
            INC SI
            INC DI
            DEC CL
			JNZ X1
			

.EXIT
END
