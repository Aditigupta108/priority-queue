#include <iostream>
using namespace std;
struct pqnode
{
public:
    int num;
    int priority;
    pqnode *next;
};
class PQ
{
    pqnode *start;

public:
    PQ() { start = NULL; }
    void enqueue(int n,int pr)
    {
        pqnode *t = new pqnode();
        t->num = n;
        t->priority = pr;
        t->next = NULL;
        if (start = NULL)
        {
            start = t;
            return;
        }
        if (t->priority < start->priority)
        {
            t->next = start;
            start = t;
            return;
        }
        pqnode *temp = start;
        while (temp->next != NULL)
        {
            if (t->priority < temp->next->priority)
            {
                break;
            }
            else
            {
                temp = temp->next;
            }
        }
        t->next = temp->next;
        temp->next = t;
    }
    int dequeue()
    {
        if (start == NULL)
        {
            cout << "EMPTY" << endl;
            return 0;
        }
        pqnode *t = start;
        start = start->next;
        int x = t->num;
        delete t;
        return x;
    }
};
int main()
{
    PQ prqu;
    prqu.enqueue(64,4);
    prqu.enqueue(75,5);
    prqu.enqueue(2,2);
    cout << "DEQUEUED ELEMENT IS " << prqu.dequeue();
}
