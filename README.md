# Distribute-Coins-in-Binary-Tree

You are given the root of a binary tree with n nodes where each node in the tree has node.val coins. There are n coins in total throughout the whole tree.
In one move, we may choose two adjacent nodes and move one coin from one node to another. A move may be from parent to child, or from child to parent.
Return the minimum number of moves required to make every node have exactly one coin.

class Solution:
    def __init__(self):
        self.ans = 0

    def distributeCoins(self, root: TreeNode) -> int:
        self.ans = 0
        self.countSteps(root)
        return self.ans

    def countSteps(self, root: TreeNode) -> int:
        if root is None:
            return 0
        leftCoins = self.countSteps(root.left)
        rightCoins = self.countSteps(root.right)
        self.ans += abs(leftCoins) + abs(rightCoins)
        return (root.val - 1) + leftCoins + rightCoins
