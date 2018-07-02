public class Solution {
    /**
     * @param s: a string
     * @param t: a string
     * @return: true if the characters in s can be replaced to get t or false
     */
    public boolean isIsomorphic(String s, String t) {
        // write your code here

        int[] map = new int[256];
        char[] sa = s.toCharArray();
        char[] ta = t.toCharArray();
        for (int i = 0; i < s.length(); i++) {
            if (map[sa[i]] == 0) {
                map[sa[i]] = ta[i];
            }
            else {
                if (map[sa[i]] != ta[i]) {
                    return false;
                }
            }
        }
        int[] map2 = new int[256];
        for (int i = 0; i < t.length(); i++) {
            if (map2[ta[i]] == 0) {
                map2[ta[i]] = sa[i];
            }
            else {
                if (map2[ta[i]] != sa[i]) {
                    return false;
                }
            }
        }
        
        return true;
    }
}
