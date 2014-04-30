Lab_5
=====
#####Discussion of 1st Program Operation

The First program would start with a value of 8, increment by 1, and then display the new number, 9. This would keep
repeating,as PRISM would recognize numbers above 8 as negative, and would stop at 0 and keep displaying 0. So the output should read: 9,A,B,C,D,E,F,0. This is important for recognizing cases or passwords of sorts. The JN served as a check, and by using it we could set conditions for certain instructions to be read. Again, a password of sorts.

#####Discussion of 1st Program Instruction Cycles

#####Answers to PRISM Questions

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
