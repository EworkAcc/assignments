Here as some possible things that may look like mistakes.
In the output file it looks as if there are 4 characters with no meaning and 1 U, but really there is two spaces in between the characters with no meaning. It is caused as the value after xoring them isn't a value that has an ascii representation or doesn't work. Decryption still works though so it should prove that the xor is working.
