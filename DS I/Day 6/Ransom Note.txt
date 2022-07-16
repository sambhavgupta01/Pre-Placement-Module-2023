class Solution {
public:
    bool canConstruct(string ransomNote, string magazine) {
        map<char, int> pool;
        for (char c: magazine) {
            pool[c]++;
        }
        for (char c: ransomNote) {
            if (--pool[c] < 0) {
                return false;
            }
        }
        return true;
    }
};