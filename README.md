# Two-Sum-IV---Input-is-a-BST
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def findTarget(self, root: Optional[TreeNode], k: int) -> bool:
        if root is None:
            return False
        def add(root,r):
            if root is None:
                return
            r.append(root.val)
            add(root.left,r)
            add(root.right,r)
        r=[]
        add(root,r)
        r.sort()
        n=len(r)
        left=0
        right=n-1
        while left<right:
            if r[left]+r[right]==k:
                return True
            elif r[left]+r[right]>k:
                right=right-1
            else:
                left=left+1
        return False
