class Solution
{
public:
    vector<int>v1,v2;
    void inorder(Node* r,vector<int>&v){
        if(!r)return;
        inorder(r->left,v);
        v.push_back(r->data);
        inorder(r->right,v);
    }
    
    int countPairs(Node* r1, Node* r2, int x)
    
    {
        int c=0;
        inorder(r1,v1);
        inorder(r2,v2);
        int i=0, j=v2.size()-1;
        while(i<v1.size() and j>=0){
            if(v1[i]+v2[j]==x){
                c++;
                i++;
                j--;
            }
            else if(v1[i]+v2[j]<x){
                i++;
            }
            else{
                j--;
            }
        }
        return c;
    }
};
