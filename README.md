Leecode：

给定一个字符串 `s` ，请你找出其中不含有重复字符的 **最长子串** 的长度。(子串：是字符串连续不断的一块字符串，如"abcdefg"则"bcd"为其子串。)
class Solution {
    public int lengthOfLongestSubstring(String s) {
        Set<Character> map = new HashSet<>();
        int right = 0;
        int ans = 0;
        int len = s.length();
        for (int i = 0; i < len; i++) {
            if (i != 0) {
                map.remove(s.charAt(i - 1));
            }
            while (right < len && !map.contains(s.charAt(right))) {
                map.add(s.charAt(right));
                right++;
            }
            ans = Math.max(ans, right - i);
        }
        return ans;
    }
}
