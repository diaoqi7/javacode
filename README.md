# javacode
package HibertTest;
 
public class HilberOne {
   /**
   * @param args
   */
   public int cPos(int[] data, int m, int d) {
     int[] c=new int[d];
        char[] p = new char[m];
        int[][] b = new int[m][d];
        int[] a1=new int[m];
        int[] b1=new int[m];
        int sum=0;
        for(int i=0;i<m;i++){
        a1[i]=0;
       
        }
       
        for(int i=0;i<m;i++){
        b1[i]=1;
       
        }
      
        //int[][] A = new int[m][d];
     for (int k = 0; k < d; k++) {
        int a = data[k];
        char[] temp = Integer.toBinaryString(a).toCharArray();
       
        for (int l = 0; l < m; l++) {
          if (temp.length < m) {
             for (int n = 0; n < m - temp.length; n++) {
               p[n] = '0';
             }
          } else {
             p[l] = temp[l];
          }
       
        }
         for (int j = 0; j < m; j++) {
          b[j][k] = p[j] - '0';
            //System.out.print("b"+j+k+"=:"+b[j][k]+" ");
        }
         //System.out.println();
     }
     for(int i=0;i<m-1;i++){
       
        for(int j=0;j<d;j++){
         
          for(int k=0;k<m;k++){
             if(b[k][i]==a1[k] || b[k][i]==b1[k] ){
               c[i]=d-1;
             }else if(b[j][i]==1){
               c[i]=j;
               break;
             }
          }
        }
       
        sum=sum+(c[i]-1);
     }
     System.out.println(sum);
     return sum;
    
   }
 
   public void xOr(int[] a, int[] b) {
     int[] c = new int[a.length];
     for (int i = 0; i < a.length && i < b.length; i++) {
        c[i] = a[i] ^ b[i];
        // System.out.print(c[i]);
     }
   }
 
   public void computeHilbert(int[] data, int m, int d) {
     int[][] b = new int[m][d];
     char[] p = new char[m];
     for (int k = 0; k < d; k++) {
        int a = data[k];
        char[] temp = Integer.toBinaryString(a).toCharArray();
       
        for (int l = 0; l < m; l++) {
          if (temp.length < m) {
             for (int n = 0; n < m - temp.length; n++) {
               p[n] = '0';
             }
          } else {
             p[l] = temp[l];
          }
        //System.out.println(p[l]);
        }
       
         for (int j = 0; j < m; j++) {
          b[j][k] = p[j] - '0';
            //System.out.println("b"+j+k+"=:"+b[j][k]);
        }
     }
     int[][] A = new int[d][m];
     int[] w = new int[d];
     int[] t = new int[d];
     int[] o = new int[d];
     int[] O = new int[d];
     int sum=0;
     for (int i = 0; i < m; i++) {
        for (int j = 0; j < d; j++) {
          A[i][j] = b[i][j];
          if (i == 0) {
             w[i] = 0;
          } else {
             w[i] = (w[i - 1]) ^ (t[i - 1]);
          }
          O[i] = (A[i][j]) ^ (w[i]);
          if (i == 0) {
             o[0] = O[0];
          } else {
             // o[i]=
          }
        }
     }
 
   }
 
   public static void main(String[] args) {
     // TODO Auto-generated method stub
     HilberOne h = new HilberOne();
     int[] a = {3,1};
     h.computeHilbert(a, 2, 2);
     h.cPos(a, 2, 2);
   }
}