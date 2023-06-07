## There are two variations of sliding window.
1. Fixed size window
2. variable size window

### 1. Fixed size window

Problem 1 - https://practice.geeksforgeeks.org/problems/max-sum-subarray-of-size-k5313/1 <br>
Problem 2 - https://practice.geeksforgeeks.org/problems/first-negative-integer-in-every-window-of-size-k3345/1 <br>
Problem 3 - https://practice.geeksforgeeks.org/problems/count-occurences-of-anagrams5839/1 <br>
Proble 4 - https://practice.geeksforgeeks.org/problems/max-sum-subarray-of-size-k5313/1 <br>

```cpp
Problem 1-
  
class Solution {
public:
    long maximumSumSubarray(int K, vector<int>& Arr, int N) {
        int i = 0, j = 0;
        long sum = 0;
        long maxi = INT_MIN;

        while (j < N) {
            sum += Arr[j];  // calculation for j
            if (j - i + 1 < K)
                j++;
            else if (j - i + 1 == K) {
                maxi = max(maxi, sum);
                sum = sum - Arr[i];  // calculation for i
                i++;
                j++;
            }
        }
        return maxi;
    }
};




Problem 2- 
  
vector<long long> printFirstNegativeInteger(long long int A[], long long int N, long long int K) {                                                                                   
    long long int i = 0 , j = 0;
    vector<long long> res;
    queue<long long> temp;
    
    while(j < N){
        if(A[j] < 0)  temp.push(A[j]);
        
        if(j-i+1 < K)  j++;
        
        else if(j-i+1 == K){
            if(temp.size() == 0) res.push_back(0);
            else
                res.push_back(temp.front());
                if(A[i] < 0)
                temp.pop();
                i++;
                j++;
            
        }
    }
        
        return res;
 }


Problem 3- 

class Solution{
public:   // TC-O(n)  SC-O(n)
	int search(string pat, string txt) {
	    int patSize = pat.size() , txtSize = txt.size();
	    int i = 0 , j = 0 , ans = 0;
	    unordered_map<char , int> umap;
	    for(auto i : pat){
	        umap[i]++;
	    }
	    int mapSize = umap.size();
	    while(j < txtSize){
	        if(umap.find(txt[j]) != umap.end()){
	            umap[txt[j]]--;
	            if(umap[txt[j]] == 0){
	                mapSize--;
	            }
	        }
	        
	   if(j-i+1 < patSize){
	       j++;
	   } else if(j-i+1 == patSize){
	            if(mapSize == 0)  ans++;
	            if(umap.find(txt[i]) != umap.end()){
	                umap[txt[i]]++;
	                if(umap[txt[i]] == 1){
	                    mapSize++;
	                }
	            }
	            i++;
	            j++;
	            
	        }
	    }
	    return ans;
	}

};

# Problem 4- 
  
  class Solution{   
public:
    long maximumSumSubarray(int K, vector<int> &Arr , int N){
        
        int i = 0 , j = 0 ; long sum = 0;
        long maxi = INT_MIN;
     
     while(j < N){
         sum += Arr[j];  //calculation for j
         if(j-i+1 < K) j++; 
                               //For getting window size
         else if(j-i+1 == K)
         {
             maxi = max(maxi , sum);
             sum = sum - Arr[i];     // calculation for i
             i++;
             j++;
         }
     }
        return maxi;
    }
};

  
