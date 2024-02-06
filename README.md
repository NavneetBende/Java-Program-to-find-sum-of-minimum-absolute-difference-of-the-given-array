Sum of minimum absolute difference of the array
To find sum of minimum absolute difference of the given array is discussed here. An array of distinct elements is given as input and to calculate minimum absolute difference for an element “a” and x is its index, and there is an array of y different integer we will use formula.

Java Program to find sum of minimum absolute difference of the given array
Method Discussed :
Method 1 : Using Brute Force Approach
Method 2 : Using Efficient solution
Method 1 :
Take a variable say result = Integer.MAX_VALUE, to hold the required minimum sum.
Run an outer loop from index 0 to n,
Create a variable say sum = 0,
Run an inner loop from index 0 to n,
Set, sum += Math.abs(arr[i]-arr[j])
After complete iteration of inner loop set,
result = Math.min(result, sum).
Print result.
Method 1 : Code in Java
//Write a program to find sum of minimum absolute difference of the given array in Java
import java.util.Arrays;
 
public class Main {
     
    static int sumOfMinAbsDifferences(int arr[] ,int n)
    {
        
        int result = Integer.MAX_VALUE;
         
        for (int i = 0; i < n; i++){
            int sum =0;
            for(int j=0; j<n; j++){
                sum += Math.abs(arr[i] - arr[j]);
            }
            
            result = Math.min(sum, result);
        }
            
        return result;
    }    
 
    // Driver code
    public static void main(String args[])
    {
        int arr[] = {2, 4, 5, 3};
        int n = arr.length;
         
        System.out.println( "Required Minimum Sum is " + sumOfMinAbsDifferences(arr, n));
    }
}
Output
Required Minimum Sum is 4
Related Pages
Determine Array is a subset of another array or not

Determine can all numbers of an array be made equal

Sort an array according to the order defined by another array 

Replace each element of the array by its rank in the array

Finding equilibrium index of an array

Method 2 :
Sort the array using inbuilt sort() function.
For the element at 0 index of array its min absolute difference is calculated using the element at index 1.
For the element at last index its min absolute difference is calculated using the 2nd last array element.
For the rest of the array elements, 1 <= i <= n-2, minimum absolute difference for an element at index i is calculated as: minAbsDiff = min( abs(arr[i] – arr[i-1]), abs(ar[i] – arr[i+1]) ).
Method 2 : Code in Java
//Write a program to find sum of minimum absolute difference of the given array in Java
import java.util.Arrays;
 
public class Main {
     
    static int sumOfMinAbsDifferences(int arr[] ,int n)
    {
         
        // sort the given array
        Arrays.sort(arr);
         
        // initialize sum
        int sum = 0;
         
        sum += Math.abs(arr[0] - arr[1]);
         
        sum += Math.abs(arr[n-1] - arr[n-2]);
         
        for (int i = 1; i < n - 1; i++)
            sum +=Math.min(Math.abs(arr[i] - arr[i-1]),Math.abs(arr[i] - arr[i+1]));
             
        // required sum
        return sum;
    }    
 
    // Driver code
    public static void main(String args[])
    {
        int arr[] = {2, 4, 5, 3};
        int n = arr.length;
         
        System.out.println( "Required Minimum Sum is " + sumOfMinAbsDifferences(arr, n));
    }
}
Output
Required Minimum Sum is 4
