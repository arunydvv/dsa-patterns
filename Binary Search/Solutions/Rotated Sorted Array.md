int searchPivot(int[] nums) {
        int start = 0,pivot;
        int end = nums.length - 1;
        while(start <= end){
            int mid  = start + (end - start)/2;
            if (mid < end && nums[mid] > nums[mid + 1]) return mid;
            if (start < mid && nums[mid] < nums[mid - 1] ) return mid -1;
            else if (nums[mid] <= nums[start]) end = mid -1;
            else start = mid + 1;
        }
        return -1; 
    }


class Solution {
    public int search(int[] nums, int target) {
        int start = 0;
        int end = nums.length -1;

        while (start <= end){
            int mid = start + (end- start)/2;
            if (nums[mid] == target) return mid;
            if (nums[start] <= nums[mid]) {  // Left half is sorted
            if (nums[start] <= target && target < nums[mid]) {
                end = mid - 1;
            } else {
                start = mid + 1;
            }
        }
        else {  // Right half is sorted
            if (nums[mid] < target && target <= nums[end]) {
                start = mid + 1;
            } else {
                end = mid - 1;
            }
        }
        }
        return -1;

    }
}