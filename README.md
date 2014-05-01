Lab_5
=====
#####Discussion of 1st Program Operation

The First program would start with a value of 8, increment by 1, and then display the new number, 9. This would keep
repeating,as PRISM would recognize numbers above 8 as negative, and would stop at 0 and keep displaying 0. So the output should read: 9,A,B,C,D,E,F,0. This is important for recognizing cases or passwords of sorts. The JN served as a check, and by using it we could set conditions for certain instructions to be read. Again, a password of sorts.

#####Discussion of 1st Program Instruction Cycles


![alt text] (http://i61.tinypic.com/2mnqk5e.png)

5ns-15ns Fetch, This fetches the number from the IR and directs the next opcode, In this case, IRLD is loaded as a 7 from the Data.
15ns-25ns Decodes, Interprets the number as a specific opcode, in this case, the Opcode is 7, or LDAI. It then determines
if more data will be needed from memory to execute the opcode. In this case, no more memory is needed so we go to next phase
25ns-35ns Immediate Execute, the PC is place on the addr bus, the first operand goes on data bus, and the lower 3 bits of the opcode go the the ALU as OPSel. The result is thrown on the Acc, and the PC is incremented to the next instruction. Then we do Fetch again

35ns-45ns Fetch, Number 6 is read from IR
45ns-55ns Decode, Number is is interpreted as Opcode 6, or addi. In this case, more memory is not needed so we go to immediate execute
55ns-65ns Immediate Execute, Same process as above in the previous immediate execute. The PC increments and we Fetch again

65ns-75ns Fetch, Number 4 is read from the IR
75ns-85ns Decode, Number 4 is interpreted to be out 3, more data from memory will be needed to execute this instruction

![alt text] (http://i57.tinypic.com/1zn02z9.png)

85ns-95ns Decode LoAddr, The PC increments, The operand, or 4 bit port number, is stored into MARLo. The data to be output is stored on the data bus for later as well. Since the IR reads 4, this means we will go to Direct IO execute.
95-105ns Direct I/O Execute, The controller sends the lower 3 bits of the Opcode to the ALU via OpSel. The MARLo register holding which port will be used as output is placed on the Addr bus. Since this is an OUT operation, the value in the Acc is placed on the data bus via EnAccBuff. Then we moved to Fetch

105ns-115 Fetch, Number b is read from the IR
115ns-125 Decode, Number b is interpreted as Opcode b, or jn. In this case more data will be needed to complete the instruction
125ns-135ns Decode LoAddr, Same as the Decode LoAddr discussed above, except in this case the IR reads b, so the next instruction will be Decode HiAddr
145ns-155ns Decod HiAddr, The PC increments, the second operand is stored on the data bus, the upper 4 bits of the memory location are stored into MARHi. The IR reads b, so this means that the next phase will be JMP execute
135ns-145ns JMP Execute, The IR is holding a JN Opcode, the value in the MAR is then loaded in the PC if A is less than 0. In this case, A is less than 0 so the JN is executed
155ns-165ns Fetch, Number 6 is read from the IR. This is a loop and it will keep repeating from the beginning of 35ns and onwards until we get a positive number. Once we get a positive number, the program will jump to the end instruction and keep looping from there.
165-... Loop keeps repeating and jumps to end eventually.

#####Answers to PRISM Questions

1
2
3
4
5


#####Notes
The Demonstration for the 2nd Program involving counting up and down was delayed due to PRISM not updating the address of its opcodes. 
This was likely caused from copying and pasting instructions incorrectly, so even though it might have said JMP for an
instruction, the value for the instruction would be a 5 instead of the 9 required for the jump. This caused the PRISM program
to malfunction. I ended up finishing this part of the program about 10 minutes after we were released from the class it was
due on after Capt Trimble helped me troubleshoot the program.

The A Funct. program was finished on the next day after class since I had some time to burn and I figured more practice 
could not hurt. This program counted up by 1's, 2's, or 3's depending on what was input on the switches. The 2 digit
counte would keep counting until it rolled over. I.E. it would go 89,92,95,98,01,04... I did not put a countdown function
on the program, but I think I could have by creating a condition which would invert the input value and then keep adding it
to its respective register as the program normally did. Originally I wanted to have it count by the numbers 4-9, but I ran
out of room to code which is why I stuck with 1-3 for counting.
