class Solution {
    public int searchInsert(int[] nums, int target) {
        int start = 0;
        int end = nums.length - 1;
        if(target > nums[end]) return end+1;
        if(target < nums[start]) return 0;
        while (start <= end) {
            int mid = start + (end - start)/2;
            if (nums[mid] == target) return mid;
            else if (nums[mid] < target) start = mid + 1;
            else end = mid - 1;
        }
        return start;
    }
}


