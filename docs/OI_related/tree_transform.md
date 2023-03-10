## background
在解决很多树形问题的时候会遇到多叉树，但是多叉树在很多时候解决起来很麻烦。根据数学家烧水的思想可以将多叉树转化为二叉树求解。同时该方法也可以将森林转化为一棵二叉树，非常实用。

## solution
把多叉树的第一个儿子放在左儿子，其他兄弟放在右儿子，称为“左兄弟右儿子”。

至于代码实现，输入一条边 $(u,v)$ ，表示 $v$ 是  $u$ 的孩子，如果 $u$ 的左儿子为空，就将 $v$ 放在左儿子，否则循环知道右儿子不为空放进去。
```cpp
for(int i=1;i<=n;i++){
    cin>>v>>w;
    if(ch[v][0]==0) ch[v][0]=i;
    else {
    int temp=ch[v][0];
        while(ch[temp][1]!=0) temp=ch[temp][1];	     
        ch[temp][1]=i;
    }
    c[i]=w;
    in[ch[i][0]]++;
    in[ch[i][1]]++;
}

```
但是当 $n$ 的范围很大时，这个预处理的时间复杂度也会增大，很不划算。所以对于这种还有一个优化操作，我们还可以用类似储存链式前向星的方法，让父亲的左孩子为读入的孩子，然后这个孩子的右孩子是父亲的之前第一个左孩子。

```cpp
for (int i=1;i<=m;i++){
    cin>>a>>b     //a是b的孩子
    tree[a].r=tree[b].l;    //把b的左孩子给a的右孩子
    tree[b].l=a;     //把a给b的左孩子
}
```
~~但是吧，我对这种方法还是没有研究得很透~~