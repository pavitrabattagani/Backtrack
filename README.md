# Backtrack
Leetcode-79

class Solution {
    public List<List<Integer>> subsets(int[] nums) {
        List<List<Integer>> ans= new ArrayList();
            backtrack(0,nums,new ArrayList<>(),ans);
            return ans;
        }
        private void backtrack(int ind,int[]nums,ArrayList<Integer>path,
        List<List<Integer>>ans){
            if(ind==nums.length){
                ans.add(new ArrayList<>(path));
                return;
            }
            path.add(nums[ind]);
            backtrack(ind+1,nums,path,ans);
            path.remove(path.size()-1);
            backtrack(ind+1,nums,path,ans);
        }
    }
