# Mseries-1


//TC: O(n *100*100)
//SC: O(100) i.e constant O(1)
class Solution {
    public int threeSumMulti(int[] arr, int target) {
        int mod = 1_000_000_007;
        long result = 0;
        long count[] = new long[101];
        
        //taking counts
        for(int i: arr ) count[i]++;
        
        for(int i = 0; i <= 100; i++){
            for(int j = i; j <= 100; j++){
                int k = target - i - j;
                if(k<0 || k>100) continue;
                if(i==j && j==k){
                   result += count[i] * (count[i] - 1) * (count[i] - 2) / 6;
                }else if(i==j && j!=k){
                    result += ((count[i] * (count[i] - 1) / 2) * count[k]);
                } else if(i<j && j<k){
                    result += count[i]*count[j]*count[k];
                }
            }
        }
        
        return (int) (result%mod);
    }
}



///////TC- O(n^2)


class Solution {
    public int threeSumMulti(int[] arr, int target) {
        int mod =  1_000_000_007;
        long result = 0;
        
        for(int i = 0; i < arr.length; i++){
            int count[] = new int[101]; 
            for(int j= i+1; j < arr.length; j++){
                
                int k = target - arr[i] - arr[j];
                if(k>=0 && k<= 100 && count[k]>0){
                    result+=count[k];
                    result%=mod;
                }
                count[arr[j]]++;
            }
            
        }
        return (int)result;
    }
}
