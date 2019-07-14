import java.util.*;
import java.lang.*;
import java.io.*;
 
/* Name of the class has to be "Main" only if the class is public. */
class Main
{
	public static void main (String[] args) throws java.lang.Exception
	{
		BufferedReader br= new BufferedReader(new InputStreamReader(System.in));
		//System.out.println("Enter size of array");
		int N= Integer.parseInt(br.readLine());
		int[] arr= new int[N];
	//	System.out.println("Enter array");
		String line= br.readLine();
		String[] str= line.trim().split("\\s+");
        
		for (int i = 0; i < N; i++) {
			arr[i]= Integer.parseInt(str[i]);
		}
		int[] bitScore = new int[arr.length];
		/*minVisible[0] =0;
		for(int i=1;i<arr.length;i++){
		    minVisible[i]= Integer.MIN_VLAUE;
			for(int j=0;j<=i;j++){
			    if(arr[i]>arr[j]){
			        minVisible[i]=Maths.max(minVisible[i],minVisible[j]+1);
			    }else{
			        minVisible[i]=Maths.min(minVisible[i],minVisible[j]);
			    }
			}
		}
		System.out.print(minVisible);*/
		int maxNum = 0;
		int minNum = 0;
		for(int i=0;i<arr.length;i++){
		    maxNum = Integer.MIN_VALUE;
		    minNum = Integer.MAX_VALUE;
		    int temp = arr[i];
		    while(temp!=0){
		        if(temp%10>maxNum){
		            maxNum= temp%10;
		        }if(temp%10<minNum){
		            minNum = temp%10;
		        }
		        temp =temp/10;
		    } 
		    bitScore[i]= (maxNum*11 + minNum*7)%100;
		}
		for(int j=0;j<bitScore.length;j++){
		    System.out.print(bitScore[j]+" ");
		}
		int[] oddCount = new int[10];
		int[] evenCount = new int[10];
		//int previousOdd =bitScore[0]/10;
		//digitCount[previousOdd] = digitCount[previousOdd]+1;
		//int previousEven =bitScore[1]/10;
		//digitCount[previousEven] = digitCount[previousEven]+1;
		int pairs =0;
		for(int k=0;k<bitScore.length;k++){
		   if(k%2==0){
		       oddCount[bitScore[k]/10] = oddCount[bitScore[k]/10]+1;
		   }
		   else{
		       evenCount[bitScore[k]/10] = evenCount[bitScore[k]/10]+1;
		   }
		}for(int j=0;j<oddCount.length;j++){
		    System.out.print("o"+oddCount[j]+" ");
		    System.out.print("e"+evenCount[j]+" ");
		}
		for(int m=0; m<oddCount.length;m++){
		    if(oddCount[m]+evenCount[m]>3)
		    pairs +=2;
		    else if(oddCount[m]==3 || evenCount[m]==3){
		        pairs +=2;
		    }else{
		        if(oddCount[m]==2)
		            pairs++;
		        if(evenCount[m]==2)
		            pairs++;
		    }
		    
		}
		System.out.print(pairs);
	}
 
}
