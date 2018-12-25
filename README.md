// BinarySeacrhTree
// BinarySeacrhTree Sir Israr Assignment 
import java.util.Scanner;
public class main {
    public static void main(String[] args) {
        BinarySearchTree b = new BinarySearchTree();{
            b.Add(40);//Node
            b.Add(50);//Right
            b.Add(30);//Left
            b.Display();
            b.Find(10);//not in tree
            b.Find(50);
            b.delete(20);//not in tree
            b.delete(40);
            System.out.println();
            b.Display();                   
        }
    }       
}
class BinarySearchTree {
    private Node root;
     Node Find(int value){
        Node  n = root;
        while( n!=null)
        {
            if(n.getData() == value)
            {
                System.out.println(value +" found");
                return n;
            }
            if(n.getData() < value)
                n = n.getRight();
            else
                n= n.getLeft();
        }
        System.out.println(value +" not found");
        return null;
    }  
     private Node deleteNodeUsingRecursive(Node n,int value){
         if(n==null){
             System.out.println("Value not in tree");
             return null;
         }
         if(value==n.data){
             if (n.left == null && n.right == null) {
                return null;
             }
             if (n.right == null) {
                 return n.left;
             }

             if (n.left == null) {
                 return n.right;
             }
         }
         if(value<n.data){
              n.left= deleteNodeUsingRecursive(n.left,value);
              return n;
         }
         n.right=deleteNodeUsingRecursive(n.right,value);
         return n;
     }
     public void delete(int value){
         root=deleteNodeUsingRecursive(root,value);
     }
     void preorder(Node n){
           if( n == null ) { return;}
                       System.out.print(n.getData()+" ");
                      preorder(n.getLeft());
                      preorder(n.getRight());
        }
     void Inorder(Node n){
           if( n == null ) {System.out.println(); return;}
                       Inorder(n.getLeft());
                       System.out.print(n.getData()+" ");
                       Inorder(n.getRight());  
     }
    void postorder(Node n){
           if( n == null ) return;
                   postorder(n.getLeft());
                   postorder(n.getRight());
                   System.out.print(n.getData()+" ");  
    }
    void Add(int value){
        Node  n = root;
        if(n==null)root=new Node(value,null,null);
        else{
        while( n!=null)
        {
            if(n.getData() < value)
            {
                if(n.getRight()==null)
                    {
                    n.setRight(new Node(value,null,null));
                    break;
                    }
                else n=n.getRight();
            }
            else
            {
                if(n.getLeft()==null)
                {
                n.setLeft(new Node(value,null,null));
                break;
                }
                else n=n.getLeft();
                }
            }
        }  
    }
    void Display() {
        Scanner sc = new Scanner(System.in);
        System.out.println("Press 1 for PreOrder");
        System.out.println("Press 2 for InOrder");
        System.out.println("Press 3 for PostOrder");   
        int input = sc.nextInt();
        if (input==1)
            preorder(getRoot());
        else if(input==2)
                Inorder(getRoot());       
        else if(input==3)
                postorder(getRoot());   
                else
                System.out.println("Invalid Input");
                }
   
    Node getRoot(){
        return this.root;
    }
     void setRoot(Node n){
        this.root=n;
    }
}
class Node {
    int data;
    Node left;
    Node right;
    public Node(int d,Node l,Node r){
        this.data=d;
        this.left=l;
        this.right=r;
    }
     int getData(){
        return data;
        }
     void setData(int data){
        this.data = data;
        }
    Node getLeft(){
        return left;
        }
    void setLeft(Node left){
        this.left = left;
        }
    Node getRight(){
        return right;
        }
    void setRight(Node right){
        this.right = right;
        }
}
