# Moglix_code_dhwani
class Solution {
    public int longestValidParentheses(String s) {
        int maxLen = 0;
        Stack<Integer> stack = new Stack<>();
        stack.push(-1); // taken base for Length Calculation 
         for (int i = 0; i < s.length(); i++) {
            char c = s.charAt(i);
            if (c == '(') {
                stack.push(i);
            } else {
                stack.pop(); // deleting top most element
                 if (stack.isEmpty()) {
                    // no matching '(' found, push current index as new base
                    stack.push(i);
                } else {
                    int len = i - stack.peek();
                    maxLen = Math.max(maxLen, len);
                }
            }
        }
        return maxLen;
    }
}
