# AVL-tree-p6
Practice program
class Node:
    def __init__(self,k):
        self.key=k
        self.left=None
        self.right=None
        self.h=1
def h(n): return n.h if n else 0
def bal(n): return h(n.left)-h(n.right) if n else 0
def rr(z):
    y=z.left
    z.left=y.right
    y.right=z z.h=1+max(h(z.left),h(z.right))  y.h=1+max(h(y.left),h(y.right))
    return y
def lr(z):
    y=z.right
    z.right=y.left
    y.left=z z.h=1+max(h(z.left),h(z.right)) y.h=1+max(h(y.left),h(y.right))
    return y
def insert(r,k):
    if not r: return Node(k)
    if k<r.key: r.left=insert(r.left,k)
    else: r.right=insert(r.right,k) r.h=1+max(h(r.left),h(r.right))
    b=bal(r)
    if b>1 and k<r.left.key: return rr(r)
    if b<-1 and k>r.right.key: return lr(r)
    return r
def pre(r):
    if r:
        print(r.key,end=" ")
        pre(r.left)
        pre(r.right)
root=None
for i in [10,20,30]:
    root=insert(root,i)
pre(root)

Output:
Output:

 20 10 30
