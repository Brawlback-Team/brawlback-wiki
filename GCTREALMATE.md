# GCTRM Documentation

## Introduction
Brawl codes modding is traditionally an arduous process that involves writing ASM, converting it to hexadecimal Gecko codes, and finally creating a \*.GCT file from this. However, in recent years there has been progress made that speeds this process up; first, we had software and websites to convert the ASM to Gecko codes, but now we have a program called GCTRealMate aka GCTRM that automates the workflow from start to finish, as well as adding some quality of life functionality to writing codes. While there does not exist any official documentation from its creator DukeItOut, P+ utilizes GCTRM and has some good examples of what is possible within its source code, as well as introducing its workflow. Let's review some basic needs and how to satisfy them, as well as some new concepts introduced by GCTRM.


## Gecko Codes
**Example**  
#################  
Infinite Replays  
#################  
\* 040E5DE8 60000000  
\* 04953184 60000000  
\* 04953224 60000000  

**Explanation**  
To write pure Gecko codes for GCTRM to process, you simply write the code and add an asterisk and a space before every line of hexadecimal pairs.  
Note: Anything written in a block of hashtags like above gets commented out.

**How GCTRM Achieves This**
GCTRM reads the codes within the hexadecimal format and converts it to a format that will be inserted into the GCT file later.  

## ASM
**Example 1**  
###################################################  
Allow Pausing When Set to Off v3 [standardtoaster]  
###################################################  
HOOK @ $800505C8  
{  
  mfcr r12  
  lis r4, 0x8058; ori r4, r4, 0x4084  
  cmpwi r3, 0x0;  bne- loc_0x18  
  li r3, 0x2  
loc_0x18:  
  stw r3, 0(r4)  
  li r4, 0x8  
  mtcr r12  
}  

**Explanation**  
To write ASM codes for GCTRM to process, you simply write the PPC at the hooked location defined by the line "HOOK @ ${Address}" and between curly brackets much like a definition in C. This runs the ASM at the location defined by the hook.

**How GCTRM Achieves This**  
GCTRM reads the PPC defined and converts it into a Gecko code.
  
**Example 2**  
int 0x91E80 @ $80421B54  
  
**Explanation**  
This writes a 4 byte value 0x00091E80 to 0x80421B54.  
  
**How GCTRM Achieves This**  
GCTRM reads the injection and converts it into a RAM write Gecko code.  
  
_For more examples, examine the P+ source code and ask for clarification in the Brawl Modding Discord._

## Macros

