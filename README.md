# valid-anagram
class Solution {
    public boolean isAnagram(String s, String t) {
     if (s.length() != t.length()) {
            return false;
        }

        HashMap<Character, Integer> charCount = new HashMap<>();

        for (char c : s.toCharArray()) {
            charCount.put(c, charCount.getOrDefault(c, 0) + 1);
        }
        for (char c : t.toCharArray()) {
            if (!charCount.containsKey(c)) {
                return false;
            }
            charCount.put(c, charCount.get(c) - 1);
            if (charCount.get(c) == 0) {
                charCount.remove(c);
            }
        }
        return charCount.isEmpty();   
    }
}
