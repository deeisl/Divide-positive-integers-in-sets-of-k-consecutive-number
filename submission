#include <iostream>
#include <vector>
#include <algorithm>
#include <sstream>

using namespace std;

bool canDivideIntoSets(std::vector<int>& nums, int k) {
    if (nums.empty()) {
        return true; // An empty array can always be divided into sets.
    }

    int n = nums.size();
    std::sort(nums.begin(), nums.end());

    for (int i = 0; i < n - k + 1; i++) {
        if (nums[i + k - 1] - nums[i] == k - 1) {
            // Found a set of k consecutive numbers, remove them from the array
            nums.erase(nums.begin() + i, nums.begin() + i + k);
            // Recursively check the remaining numbers
            if (canDivideIntoSets(nums, k)) {
                return true;
            }
            // Restore the removed numbers to backtrack and try other possibilities
            for (int j = 0; j < k; j++) {
                nums.insert(nums.begin() + i + j, nums[i + j]);
            }
        }
    }

    // Check if there are enough remaining elements to form sets of size k
    if (n >= k) {
        return false;
    }

    return true;
}

int main() {
    vector<int> nums;
    int k;

    // Input the array
    string line;
    int num;
    getline(cin, line);
    istringstream iss(line);
    while (iss >> num){
        nums.push_back(num);
    }

    // Input the value of k
    cin >> k;

    // Check if it's possible to divide the array into sets of k consecutive numbers
    if (canDivideIntoSets(nums, k)) {
        cout << "true";
    } 
    else {
        cout << "false";
    }

    return 0;
}
