# BWT-кодирование
Консольная программа BWT-кодирования на примере слова АВДДABCABCСДАВСАC

```
package com.company;

import java.util.Arrays;

public class Main
{
    public static void main(String[] args) {
        char[] Z = {'A','B','D','D','A','B','C','A','B','C','C','D','A','B','C','A','C'};
        char[][] A = new char[17][17];
        char[][] B = new char[17][17];
        String[] C = new String[17];

        for (int i=0; i<Z.length; i++) {
            for (int j=0; j<Z.length; j++) {
                A[i][j]=Z[j];
            }
        }
        for (int i=0; i<A.length; i++){
            System.out.print(Z[i] + " ");
        }
        System.out.println();
        System.out.println("---------------------------------");

        for (int i=0; i<Z.length; i++) {
            for (int j=0; j<Z.length; j++) {
                if (j+i<Z.length) {
                    B[i][j+i]=A[i][j];
                }
                else {
                    B[i][j+i-Z.length]=A[i][j];
                }
            }
        }

        for (int i=0; i<Z.length; i++) {
            for (int j=0; j<Z.length; j++) {
                System.out.print(B[i][j] + " ");
            }
            System.out.println();
        }

        StringBuilder stringBuilder = new StringBuilder();
        for (int i=0; i< Z.length; i++){
            for (int j = 0; j < B[i].length; j++) {
                C[i] = String.valueOf(B[i]);
            }
        }

        String x = new String();

        for (int i = 0; i < Z.length; i++) {
            for (int j = 0; j < Z.length; j++) {
                for (int k = i+1; k < Z.length; k++) {
                    if (C[i].compareTo(C[k]) > 0) {
                        x = C[i];
                        C[i] = C[k];
                        C[k] = x;
                    }
                }
            }
        }

        System.out.println();
        System.out.println("---------------------------------");
        System.out.println();

        for (int j=0; j<Z.length; j++) {
            System.out.print(C[j] + " \n");
        }

        System.out.println();
        System.out.println("---------------------------------");

        for (int i = 0; i < Z.length; i++) {
            System.out.print(C[i].substring(0,1) + " ");
        }
    }
}

```
