https://leetcode.com/problems/combination-sum-ii/

```java
class Solution {
    private List<List<Integer>> result = new ArrayList<>();
    int N;

    private void findCombinationSum(int start, int[] candidates, int target, List<Integer> tmp) {

        if (target < 0)
            return;

        if (target == 0) {
            result.add(new ArrayList<>(tmp));
            return;
        }

        if (start >= N) {
            // can't use this condition along with target<0
            // bcz when last index is included inside result, will not come bcz that time
            // start==N
            return;
        }

        for (int i = start; i < N; i++) {
            if(i>start && candidates[i]==candidates[i-1]) continue;
            tmp.add(candidates[i]);
            findCombinationSum(i + 1, candidates, target - candidates[i], tmp);
            tmp.remove(tmp.size() - 1);
        }
    }

    public List<List<Integer>> combinationSum2(int[] candidates, int target) {
        N = candidates.length;
        Arrays.sort(candidates);
        findCombinationSum(0, candidates, target, new ArrayList<>());
        return result;
    }
}
```