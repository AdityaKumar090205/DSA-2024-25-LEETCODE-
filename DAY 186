class Solution {
public:
    int maximumGain(string s, int x, int y) {
        int n     = s.length();
        int score = 0;

        string maxStr = (x > y) ? "ab" : "ba";
        string minStr = (maxStr == "ab") ? "ba" : "ab"; 

        //First Pass
        string temp_first     = removeSubstring(s, maxStr);
        int removedPairsCount = (n - temp_first.length()) / 2;
        score                += removedPairsCount * max(x, y);


        //Second Pass
        string temp_second = removeSubstring(temp_first, minStr);
        removedPairsCount  = (temp_first.length() - temp_second.length()) / 2;
        score             += removedPairsCount * min(x, y);

        return score;
    }

private:
    string removeSubstring(string& s, string& matchStr) {
        stack<char> st;

        for (char &ch : s) {
            if (ch == matchStr[1] && !st.empty() && st.top() == matchStr[0]) {
                st.pop();
            } else {
                st.push(ch);
            }
        }

        string remainStr;
        while (!st.empty()) {
            remainStr.push_back(st.top());
            st.pop();
        }
        reverse(remainStr.begin(), remainStr.end());
        return remainStr;
    }
};

