#include "stdio.h"
#include "string.h"

char binTotal[1000]; //an array containing our total binary string for the inputted hex number
char output[1000]; //an array of base64 values converted from inputted hex number
char *hex[16] = {"0000", "0001", "0010", "0011", "0100", "0101", "0110", "0111", "1000", "1001", "1010", "1011", "1100", "1101", "1110", "1111"};
char *base64 = "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789+/";

// interpret(char c) returns the integer value of each inputted hex character
int interpret(char c) {
        if (c == '0') {
                return 0;
        } else if (c == '1') {
                return 1;
        } else if (c == '2') {
                return 2;
        } else if (c == '3') {
                return 3;
        } else if (c == '4') {
                return 4;
        } else if (c == '5') {
                return 5;
        } else if (c == '6') {
                return 6;
        } else if (c == '7') {
                return 7;
        } else if (c == '8') {
                return 8;
        } else if (c == '9') {
                return 9;
        } else if (c == 'a') {
                return 10;
        } else if (c == 'b') {
                return 11;
        } else if (c == 'c') {
                return 12;
        } else if (c == 'd') {
                return 13;
        } else if (c == 'e') {
                return 14;
        } else if (c == 'f') {
                return 15;
        } else {
                return -1;
        }
}

int main(int argc, char **argv) {
        int sizeInput = strlen(argv[1]);
        int binSize = 0;
        int outputSize = 0;

        // convert the inputted hex number to binary and concatenate it with the previous binary values stored in binTotal
        for (int c = 0; c < sizeInput; c++) {
                strcat(binTotal, hex[interpret(argv[1][c])]);
                binSize += 4;
        }


        // pad binTotal with "0000"'s if there aren't enough bits for a 64bit number
        while (sizeInput%6 != 0) {
                strcat(binTotal, hex[0]);
                sizeInput++;
                binSize += 4;

        }

        // pull out binary strings of size 6 from binTotal and get it's decimal value
        for (int t = 0; t < binSize; t+=6) {
                int sum = 0;
                int multiplier = 0;
                for (int x = 5; x >= 0; x--) {
                        sum += (binTotal[x+t]-48) *(1 << multiplier);  // multiply the binary value {0,1} by the corresponding power of 2
                        multiplier++;
                }
                // use the decimal value to get the base64 character and print it
                output[outputSize] = base64[sum];
                printf("%c", output[outputSize]);
                outputSize++;
        }
        printf("\n");
        return 0;
}
