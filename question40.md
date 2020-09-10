```java
import java.util.*;

/**
 * @PackageName :PACKAGE_NAME
 * @CLassName: Solution
 * @Description:
 * @author:GentleSnow
 * @date 2020/9/10 10:33
 */

/**
 * 给定一个数组 candidates 和一个目标数 target ，找出 candidates 中所有可以使数字和为 target 的组合。candidates 中的每个数字在每个组合中只能使用一次。
 * 说明：
 * 所有数字（包括目标数）都是正整数。
 * 解集不能包含重复的组合。 
 * 示例 1:
 * 输入: candidates = [10,1,2,7,6,1,5], target = 8,
 * 所求解集为:
 * [
 *   [1, 7],
 *   [1, 2, 5],
 *   [2, 6],
 *   [1, 1, 6]
 * ]
 * 示例 2:
 * 输入: candidates = [2,5,2,1,2], target = 5,
 * 所求解集为:
 * [
 *   [1,2,2],
 *   [5]
 * ]
 * 来源：力扣（LeetCode）
 * 链接：https://leetcode-cn.com/problems/combination-sum-ii
 * 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。
 */
class Solution {
    public List<List<Integer>> combinationSum2(int[] candidates, int target) {
        List<List<Integer>> res = new ArrayList<>();
        Arrays.sort(candidates);
        //combo函数传入需要返回的res,候选数组,目标数字,一个新的数组,一个索引
        combo(res, candidates, target, new ArrayList<Integer>(), 0);
        return res;
    }

    private void combo(List<List<Integer>> res, int[] candidates, int target, ArrayList<Integer> templist, int index) {
        if (target <= 0) {
            //不符合题意
            return;
        }
        if (target == 0) {
            res.add(new ArrayList<>(templist));
        } else {
            for (int i = index; i < candidates.length; i++) {
                templist.add(candidates[i]);
                combo(res, candidates, target - candidates[i], templist, i + 1);
                templist.remove(templist.size() - 1);
                while (i<candidates.length-1 && candidates[i] == candidates[i+1]) i++;
            }
        }
    }
}


















```



