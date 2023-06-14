1. PROGRAM INVOLVING GENERAL DATA PROCESSING INSTRUCTIONS
A) Aim : To write an Assembly Language Program to transfer contents within the registers.Software Required: Keil μVision 5 Software

  AREA PROG1, CODE, READONLY

  ENTRY

  EXPORT START

START

   MOV R1, #0

   MOV R2, #05

    MOV R3, #04

    MOVS R0, R1

   MOVEQ R0, R2            .

   MOVS R3, #0

   MOVEQ R0, R3

   MVN R2, R2

STOP B STOP

       END

  
B)      Aim: To Write a Assembly Language Program for adding two 32 bit number


        Software Required: KeilμVision 5 Software

     AREA PROG1,CODE, READONLY
     ENTRY
     EXPORT START
START
     LDR R0,=10
     LDR R1,=20
     ADD R2,R0,R1
STOP B STOP
     END




RESULT:

                        R0 = 0X0000000A

                        R1 = 0X00000014

                        R2= 0X0000001E


C) Aim: To Write a Assembly Language Program for Addition of first Ten Number.

        Software Required: Keil μVision 5


     AREA PROG2, CODE, READONLY
     ENTRY
     EXPORT START
START
     LDR R0, =10
     LDR R1, =0
     LDR R2, =1
LOOP
     ADD R1, R2, R1
     ADD R2, R2, #1
     SUBS R4, R0, R2
      BNE LOOP
     ADD R1, R2, R1
STOP B STOP
     END


RESULT:

                        R0 = 0X0000000A

                        R1 = 0X00000037

                        R2 = 0X0000000A

Algorithm:


D)      Aim: To Write a Assembly Language Program for reverse Subtraction of two 32 numbers


        Software Required: Keil μVision 5


     AREA MYCODE, CODE, READONLY
     ENTRY
      EXPORT START
START
     LDR R1, =0X11111111
     LDR R2, =0X22222222
     RSB R0, R1, R2
STOP B STOP
    END

        RESULT:


                         R2 =0X22222222

                         R1 =0X11111111

                        R1 =0X11111111



E)      Aim: To Write a Assembly Language Program to find factorial of a number


        Software Required: KeilμVision 5




     AREA PROG5, CODE, READONLY
     ENTRY
     EXPORT
START
     MOV R6, #10
     MOV R7, #1
LOOP CMP R6, #0
     MULGT R7, R6, R7
     SUBGT R6, R6, #1
     BGT LOOP
STOP B STOP
     END




RESULT

                R7=0X00375F00





     2. PROGRAMS INVOLVING MEMORY ACCESS INSTRUCTION FOR VARIOUS DATA
        SIZES AND ADDRESSING MODES

 A. Aim: To write an assembly language program to transfer data from one memory location to
    another using various addressing modes.

AREA DATATRANSFER, CODE, READONLY
ENTRY
EXPORT START
START
        LDR R0, =0x20000000
        LDR R1, =0x20000016
        LDR R2, =0x20000042
        LDRH R4,[R2]
UP     LDRB R3, [R0]
       STRB R3, [R1]
       ADD R0, R0, #1
       ADD R1, R1, #1
       ADD R3,R3,#1
       STRB R3,[R0]
       ADD R4, R4, #-1
       CMP R4, #0
        BEQ NEXT
        B UP
NEXT    LDR R5, =0X12345678
       STRB R5,[R1]
       STRH R5,[R1,#1]
       STR R5,[R1,#4]
       STOP B STOP
       END





B. Aim: To write an Assembly Language Program to perform data exchange between memory
locations.


AREA WORD,CODE,READONLY
NUM EQU 8
EXPORT START
START
        LDR R0,=0X20000000
        LDR R1,=0X2000002C
        MOV R2,#NUM
        MOV R5,#0
WORDCOPY
        LDR R3,[R0,R5]
        LDR R4,[R1,R5]
        STR R3,[R1,R5]
        STR R4,[R0,R5]
        SUBS R2,R2,#4
        ADD R5,R5,#4
        BNE WORDCOPY
        STOP B STOP
        END



RESULT

                Before Execution

                R0 =0X20000000          11       22       33   44

                R1 =0X20000050          01       02       03   04

                After Execution

                R3 `                     11      22       33   44

                R4                      01       02       03   04

                R0 =0X20000000          01       02       03   04

                R1 =0X20000050          11       22       33   04





     3. PROGRAM INVOLVING LOGICAL OPERATIONS




     A. Aim: To write a Assembly language Program to perform Logical Operations.

Software Required: Keil μ Vision 5

     AREA MYCODE,CODE,READONLY
     ENTRY
     EXPORT START
START
     LDR R0, =0X00000000
     LDR R1, =0X00000005
     LDR R2, =0X0000000F
     AND R0,R1,R2
     ORR R3,R1,R2
     EOR R4,R1,R2
     BIC R7,R2
     BIC R5, R2,R1
STOP B STOP
  END


RESULT :

                R0= 0X00000000

                R1= 0X00000005

                R3= 0X0000000F

                R4 = 0X0000000A

                R7 = 0X00000000

                R5 = 0X00000005





B. To write an Assembly Language Program for swapping the contents of the registers using logical
operations.



        Software Required:      KeilμVision 5




     AREA PROG4, CODE, READONLY
     ENTRY
     EXPORT
START
     LDR R0,=0XF631024C
     LDR R1,=0X17539ABD
     EOR R0, R0, R1
     EOR R1, R0, R1
     EOR R0, R0, R1
STOP B STOP
     END




        RESULT



                R1=0XF631024C
                R0=0X17539ABD





    4.   PROGRAMS INVOLVING DATA CONVERSION OPERATIONS.

     To Write an Assembly language Program for conversion of a number from ASCII to HEX and HEX
    to ASCII.

Software Required: Keil μ Vision 5

AREA DATA1, DATA, READONLY
DIGIT DCD & 0F
AREA DATA2, DATA, READWRITE
RESULT DCD 0
AREA PROGRAM, CODE, READONLY
ENTRY
EXPORT START
START
       LDR R0, DIGIT
       LDR R1, =RESULT
       CMP R0, #0XA    ; JUST CHANGE INTO 3A FOR HEX TO ASCII
       BLT ADD_0
       ADD R0, R0,#07   ;CHANGE ADD T0 SUB FOR HEX TO ASCII
ADD_0 ADD R0, R0,#"0" ;CHANGE ADD T0 SUB FOR HEX TO ASCII
        STR R0, [R1]
STOP B STOP
        END
RESULT :

                R0= 0X00000046 (ASCII TO HEX)

                R0= 0X0000000F (HEX TO ASCII)



5. PROGRAMS INVOLVING SHIFT AND ROTATE INSTRUCTIONS
32



     A. Aim: To Write an Assembly Language Programming to perform different types of shift and rotate
        instructions.



AREA ROTATESHIFT, CODE, READONLY

                        ENTRY

                        EXPORT START

START

                        LDR R0, =0XF0000001

                        LSLS R1, R0, #1

                        ASRS R1, R0, #1

                        RORS R2, R0, #1

                        RRXS R3, R0

STOP                    B STOP

                        END





        B. Aim: To Write an Assembly Language Program to perform swapping of content within a register
           using rotate instruction.


AREA PROG, CODE, READONLY

        ENTRY

        EXPORT START

START

        LDR R0,=0XF631024C

        ROR R1,R0,#16

        LDR R2,=0X20000000

        STRH R1,[R2]

        LDRH R3,[R2]

        ROR R4,R3,#16

        MOV R5,#2

        STR R4,[R2,R5]

STOP B STOP

        END



6. PROGRAMS TO ILLUSTRATE BIT FIELD PROCESSING INSTURUCTIONS.



       A. Aim: To write an Assembly Language Program to find the no’s of zero’s and one’s in a 32 bit
       integer.


        Software Required:      Keil μ Vision 5

AREA DATA1, DATA, READONLY
     DCB 0X0000008F
     AREA DATA2, DATA, READWRITE
ONES DCB 0
ZEROS DCB 0
     AREA PROGRAM, CODE, READONLY
     ENTRY
     EXPORT START
START
     LDR R0,=DATA1
     EOR R5, R5, R5
     EOR R6, R6, R6
     MOV R1, #32
     LDR R3,[R0]
TOP TST R3,#01
     BEQ INC_ZERO
     ADD R6,#1
     B DN
INC_ZERO
      ADD R5,#1
DN   LSR R3, #1
     SUB R1, #1
      CMP R1,#0
      BNE TOP
      LDR R0,=ZEROS
      STRB R6,[R0]
      LDR R0,=ONES
      STRB R5,[R0]
STOP B STOP
      END




RESULT:




                R5= 0X00000005

                R6= 0X0000001B



Algorithm:

        1) Initialize the Code Area

     B. Aim: To write an Assembly Language Program to check if the given number is POSITIVE/NEGATIVE

          AREA PROG2, CODE, READONLY
          ENTRY
          EXPORT START
START
       LDR R0,= -11
       TST R0, #80000000
       BEQ num_is_pos
       BNE num_is_neg
num_is_pos
       MOV R3, #0X00
       B STOP
num_is_neg
       MOV R3, #0XFF
       STOP B STOP
       END



     C. Aim: To write an Assembly Language Program to check if the given number is ODD/EVEN

          AREA PROG2, CODE, READONLY
          ENTRY
          EXPORT START
START
       LDR R0,=11
       TST R0, #1
       BEQ num_is_even
       BNE num_is_odd
num_is_even
       MOV R3, #0X00
       B STOP
num_is_odd
       MOV R3, #0XFF
STOP B STOP
       END









     7. PROGRAMS TO ILLUSTRATE PROGRAM FLOW (BRANCHING) INSTRUCTION.

     A) Aim: To Write a Assembly Language Program to Search a 32 bit number in given array, if found
     display ffffffff in r0.


         Software Required:     Keil μ Vision 5

      AREA DATA1, DATA, READONLY
ARRY DCD 0X08F, 0X012, 0X55, 0X03, 0X088
      AREA DATA2, DATA, READONLY
KEY DCD 0X088
LEN EQU 05
     AREA PROGRAM, CODE, READONLY
     ENTRY
     EXPORT START
START
     LDR R0,=ARRY
     LDR R2,=LEN
     LDR R3,=KEY
     LDR R4,[R3]
LOOP
     LDR R5,[R0]
     CMP R4,R5
     BEQ FOUND
     ADD R0,R0,#4
     SUBS R2,R2,#0X1
     BNE LOOP
     MOV R0,#0
     B STOP
FOUND MOV R0,#0XFFFFFFFF
STOP B STOP
     END



RESULT :

                R0= 0XFFFFFFFF ( Found)











     B. Aim: To Write an Assembly Language Program to find the Largest/Smallest number in an array
     of five numbers.


         Software Required:     Keil μ Vision 5

;Largest in an array
     AREA SRC, DATA, READONLY
      DCD 0x0000008F, 0x00000012, 0x00000024, 0x00000023, 0x00000011
      ALIGN
      AREA DST, DATA, READWRITE
  SPACE 02
LEN EQU 05
      AREA PROGRAM, CODE, READONLY
        ENTRY
EXPORT START
START
      LDR R6,=LEN
      LDR R0,=SRC
      SUB R6,R6,#01
      LDR R7,[R0],#04
TOP
      LDR R8,[R0],#04
      CMP R8, R7
      MOVGE R7, R8; Change to MOVLE for finding the smallest number
      SUB R6, R6,#1
      CMP R6, #00
      BNE TOP
  LDR R0,=DST
      STR R7,[R0]
STOP B STOP
       END


RESULT :

                R7 = 0X0000008F







C) Aim: To Write a Assembly language Program for sorting of an 32 bit numbers in
ascending/descending order.

Software Required:      Keil μ Vision 5


     AREA LIST, DATA, READONLY
     DCD 0x0000008F, 0x00000012, 0x00000024, 0x00000023, 0x00000011
     ALIGN
     AREA DST, DATA, READWRITE
  SPACE 10
LEN EQU 05
     AREA PROGRAM, CODE, READONLY
     ENTRY
EXPORT START
START LDR R0,=LEN
       LDR R5,=LIST
       LDR R6,=DST
  UP   LDR R1,[R5]
       STR R1,[R6]
      ADD R5,#04
      ADD R6,#04
      SUB R0,#1
      CMP R0,#00
      BNE UP
      LDR R0,=LEN
TOP2 LDR R6,=DST


       LDR R1,=LEN
       SUB R1,#1
TOP LDR R2,[R6]
       ADD R6,#4
       LDR R3,[R6]
       CMP R2,R3 ; CHANGE CMP R3,R2 FOR DESCENDING
       BLE DN
       STR R2,[R6]
       SUB R6,#4
       STR R3,[R6]
       ADD R6,#4
DN     SUB R1,#01
       CMP R1,#00
       BLE DN1
       B TOP
DN1 SUB R0,#1
       CMP R0, #00
       BLE DN2
       B TOP2
DN2 B DN2 END


Result: R6= 0x00000011, 0x00000012, 0x00000023, 0x00000024, 0x0000008F






8. PROGRAMS TO ILLUSTRATE SATURATION OPERATION (Thumb Instructions)

A. Aim: To write an Assembly Language Program to illustrate unsigned saturation instruction and clearing the
Q flag.

# PROGRAM

        AREA PROG, CODE, READONLY

ENTRY

        EXPORT START

START

        LDR R1,=0XFFFF8000

        USAT R2,#16,R1

        MRS R0,APSR

        BIC R0,R0,1<<27

        MSR APSR_nzcvq,R0

        LDR R1,=0X00030000

        USAT R3, #16, R1

        MRS R0, APSR

        BIC R0,R0,1<<27

        MSR APSR_nzcvq,R0

        LDR R1,=0X00001234

        USAT R4, #16,R1

        MRS R0,APSR

        BIC R0,R0,1<<27

        MSR APSR_nzcvq,R0

 STOP B STOP

        END




PROGRAM

        AREA PROG, CODE, READONLY

ENTRY

        EXPORT START

START

        LDR R1,=0XFFFF7FFF

        SSAT R2,#16,R1

        MRS R0,APSR

        BIC R0,R0,1<<27

        MSR APSR_nzcvq,R0

        LDR R1,=0X00030000

        SSAT R3, #16, R1

        MRS R0,APSR

        BIC R0,R0,1<<27

        MSR APSR_nzcvq,R0

        LDR R1,=0X00001234

        SSAT R4, #16,R1

        MRS R0,APSR

        BIC R0,R0,1<<27

        MSR APSR_nzcvq,R0

STOP B STOP

        END







     9. PROGRAMS INVOLVING FLOATING POINT INSTRUCTIONS


Aim: To Write an Assembly language Program to perform Floating Point Calculations.

Software Required: Keil μ Vision 5

AREA PGM, CODE, READONLY
     ENTRY
     EXPORT START
START
     LDR r0,=0XE000ED88
     LDR r1,[r0]
     ORR r1,r1,#(0XF<<20)
     STR r1,[r0]
  LDR R1,=0X0000000A
     VMOV.F32 S7,#0X41280000
     VCVT.F32.U32 S17,S17
     VMOV.F32 S8,#0X40200000
     VMOV.F32 S9,#0X40200000
     VADD.F32 S10,S8,S9
     VMUL.F32 S11,S8,S7
     VSUB.F32 S12,S11,S10
     VNEG.F32 S13,S12
     VABS.F32 S14,S13
     VDIV.F32 S15,S11,S10
     VMLA.F32 S11,S8,S9
LOOP B LOOP
     END
RESULT :

The Assembly Language Program for Floating Pont operations are Performed.




                         
