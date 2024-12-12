# lab6

import java.util.Scanner; 
public class BellmanFord 
{ 
    private int d[]; 
    private int nov; 
    public static final int MAX_VALUE = 999; 
  
    public BellmanFord(int nov) 
    { 
        this.nov = nov; 
        d = new int[nov + 1]; 
    } 
  
    public void BellmanFordEvaluation(int s, int am[][]) 
    { 
        for (int n = 1; n <= nov; n++) 
        { 
            d[n] = MAX_VALUE; 
        } 
  
        d[s] = 0; 
        for (int n = 1; n <= nov - 1; n++) 
        { 
            for (int sn = 1; sn <= nov; sn++) 
            { 
                for (int dn = 1; dn <= nov; dn++)  
  {  
   if (am[sn][dn] != MAX_VALUE)  
   {  
    if (d[dn] > d[sn] + am[sn][dn]) 
                              d[dn] = d[sn] + am[sn][dn]; 
                 } 
                } 
            } 
        } 
for (int sn = 1; sn <= nov; sn++) 
        { 
            for (int dn = 1; dn <= nov; dn++) 
     { 
   if (am[sn][dn] != MAX_VALUE)  
   {  
   if(d[dn] > d[sn] + am[sn][dn]) 
 
                        { 
    System.out.println("The Graph contains negative egde cycle"); 
    break; 
   } 
                } 
            } 
        } 
  
        for (int v = 1; v <= nov; v++) 
        { 
            System.out.println("Distance of source  " + s + " to " + v + " is " + d[v]); 
        } 
    } 
  
    public static void main(String args[]) 
    { 
        int nov = 0; 
        int s; 
        Scanner scanner = new Scanner(System.in); 
  
        System.out.println("Enter the number of vertices"); 
        nov = scanner.nextInt(); 
  
        int am[][] = new int[nov + 1][nov + 1]; 
        System.out.println("Enter the adjacency matrix"); 
        for (int sn = 1; sn <= nov; sn++) 
        { 
            for (int dn = 1; dn <= nov; dn++) 
            { 
                am[sn][dn] = scanner.nextInt(); 
if (sn == dn) 
{ 
am[sn][dn] = 0; 
continue; 
} 
if (am[sn][dn] == 0) 
{ 
am[sn][dn] = MAX_VALUE; 
} 
} 
} 
System.out.println("Enter the source vertex"); 
s = scanner.nextInt(); 
BellmanFord bellmanford = new BellmanFord(nov); 
bellmanford.BellmanFordEvaluation(s, am); 
scanner.close();  
} 
}
