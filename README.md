# Calculate-Code
Binary_Tree_Code
class TreeNode():
    #__init__定義初始化屬性 以及 狀態,簡單來說就是創建一個類實例化
    def __init__(self,value):
        self.value = value
        self.left_Node = None
        self.right_Node = None
#二元樹搜尋類別宣告
class Binary_Tree():
    #建立空的二元搜尋樹
    
    def __init__(self):
        self.rootNode = None
    #利用傳入一個陣列參數來建立二元樹
    
    def __init__(self,data):
        for i in range(len(data)):
            self.Add_Node_To_Tree(data[i])
    def Add_Node_To_Tree(self,value): 
        #這裡開始
        currentNode = self.rootNode
        if self.rootNode == None:
            self.rootNode = TreeNode(value)
        
        #建立二元數
        else:
            if value < currentNode.value :
                if currentNode.left_Node == None:
                    currentNode.left_Node = TreeNode(value)
                    return 
                else:
                    currentNode = currentNode.left_Node
                
            else:
                if currentNode.right_Node == None:
                    currentNode.right_Node = TreeNode(value)
                else:
                    currentNode = currentNode.right_Node
        #到這裡結束 皆是屬於分配數值位於左右子樹方向
class Expression_Tree():

    
    def __init__(self,information,index):
        self.rootNode = self.create(information, index)

    #create方程式
    
    def create(self,sequence,index):
        if index >= len(sequence):
            return None
        else:
            # ord 返回一串 unicode編碼
            tempNode = TreeNode((ord)(sequence[index]))
            #建立左子樹
            tempNode.left_Node = self.create(sequence,2*index)
            #建立右子樹
            tempNode.right_Node = self.create(sequence,2*index+1)
            return tempNode
    #----------------------------------------------------------------
    def preOrder(self,node): #前序走訪
        if node != None:
            print((chr)(node.value),end='')
            self.preOrder(node.left_Node)
            self.inOrder(node.right_Node)
    
    def inOrder(self,node): #中序走訪
        if node != None:
            self.inOrder(node.left_Node)
            print((chr)(node.value),end='')
            self.inOrder(node.right_Node)
    
    def postOrder(self,node): #後序走訪
        self.postOrder(node.left_Node)
        self.postOrder(node.right_Node)
        print((chr) (node.value),end='')
    
    def condition(self,oprator,num1,num2):
        if oprator =='*':
            return(num1 * num2)
        elif oprator =='/':
            return(num1 / num2)
        elif oprator =='+':
            return(num1 + num2)
        elif oprator=='-':
            return(num1 - num2)
        elif oprator=='%':
            return(num1 % num2)
        else: 
            return -1                                                 
    #------------------------------------------------------------------
    def answer(self,node):
        firstnumber = 0
        secondnumber = 0
        if node.left_Node == None and node.right_Node == None:
            return node.value -48
        else:
            firstnumber = self.answer(node.left_Node)
            secondnumber = self.answer(node.right_Node)
            return self.condition((chr)(node.value),firstnumber,secondnumber)
