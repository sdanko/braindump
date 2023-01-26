# Base64 encoding

Base64 is a binary to a text encoding scheme that represents binary data in an ASCII string format. 
It is designed to carry data stored in binary format across the network channels.

The particular choice of base is due to the history of character set encoding: one can choose a set of 
64 characters that is both part of the subset common to most encodings, and also printable. 
This combination leaves the data unlikely to be modified in transit through systems, 
such as email, which were traditionally not 8-bit clean.

Base64 mechanism uses 64 characters to encode. These characters consist of:
1. 10 numeric value: i.e., 0,1,2,3,...,9 
2. 26 Uppercase alphabets: i.e., A,B,C,D,...,Z 
3. 26 Lowercase alphabets: i.e., a,b,c,d,...,z 
4. 2 special characters (these characters depends on operating system): i.e. +,/

Base64 converts binary to text. If you want to convert text to a base64 format, you'll need to 
convert the text to binary using some appropriate encoding (e.g. UTF-8, UTF-16) first.

## 8-bit clean

"Eight-bit clean" is a term which describes a computer system that deals correctly with extended 
character sets which (unlike ASCII) use all eight bits of a byte. Up to the early 1990s, 
many programs and communications systems used to assume that all characters have codes in the range
0 to 127. This leaves the top bit of each byte free for use as a parity bit or some kind of flag bit.
These assumptions make such systems unusable on text data that contains characters with higher character 
codes, which is commonplace in non-English-speaking countries with larger alphabets.

If a binary file is transmitted via a communications link which is not eight-bit clean, it will be corrupted.

Resources:
- https://levelup.gitconnected.com/what-is-base64-encoding-4b5ed1eb58a4
- https://stackoverflow.com/questions/201479/what-is-base-64-encoding-used-for