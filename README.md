/*        Scroll below to see JAVA code also        */
/*

    Company Tags  : Google, Facebook, Apple, Goldman Sachs, Amazon
    Leetcode Link : https://leetcode.com/problems/design-circular-queue/
*/


/***************************************************************** C++ *****************************************************************/
//Approach-1 (Using Array)
//T.C : O(1)
//S.C : O(k)

class MyCircularQueue {
public:
    int *arr;
    int front, rear, size;


    MyCircularQueue(int k) {
       arr = new int[k];
        front = -1;
        rear = -1;
        size = k;
    }
    
    
    bool enQueue(int value) {
        if(isFull()){
            return false;
        }
        if (isEmpty()){
            rear = front = 0;
        }
        else{
         rear = (rear + 1) % size;
        }
         arr[rear] = value;
         return true;

    }
    
    bool deQueue() {
        if(isEmpty()){
            return false;
        }
        if(rear == front){
            rear = front = -1;
        }
        else{
        front = (front + 1) % size;
        }
        return true;
    }
    
    int Front() {
        if(isEmpty())
        {
            return -1;
        }        
         return arr[front];
    }
    
    int Rear() {
         if(isEmpty())
        {
            return -1;
        }
        return arr[rear];
    }
    
    bool isEmpty() {
      return front == -1;
    }
    
    bool isFull() {
        if((rear + 1) % size == front){
            return true;
        }
    else{
        return false;
        }
    }
};
