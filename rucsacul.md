#Problema rucsacului

- n obiecte cu greutate si castig
- avem rucsac cu greutate G cunoscut

Aflsa castigul maxim obtinut prin transportuyl obiectelor date astfel incat sa nu depasesc capacitatea maxima a rucsacului si stiind ca putem fractiona obiectele

###Code c++

```c++
#include <iostream>
#include <string>

using namespace std;

struct object{
    float val;
    float g;
    float ratio;
    int nr;
}obiecte[20];

int n, rucsac;

void citire(){
    freopen("date.in", "r", stdin);
    cin>>n>>rucsac;
    int x, y;
    string aux;
    for (int i = 0; i < n; ++i) {
        cin >> x >> y;
        obiecte[i].val=x;
        obiecte[i].g=y;
        obiecte[i].ratio = (float)x/y;
        obiecte[i].nr=i+1;
    }
}

void sort(){
    for (int i = 0; i < n-1; ++i) {
        for (int j = i+1; j < n; ++j) {
            if(obiecte[i].ratio<obiecte[j].ratio){
                object aux = obiecte[i];
                obiecte[i]= obiecte[j];
                obiecte[j]=aux;
            }
        }
    }
}

void prelucare(){
    int castig = 0;
    for (int i = 0; i < n && rucsac>0; ++i) {
        if(obiecte[i].g<=rucsac) {
            cout << obiecte[i].nr << " 100% " << endl;
            castig += obiecte[i].val;
            rucsac -= obiecte[i].g;
        }else{
            cout<<obiecte[i].nr<<" "<<rucsac*100.0/obiecte[i].g<<"%"<<endl;
            castig+=obiecte[i].ratio*rucsac;
            rucsac = 0;
        }
    }
}

int main() {
    citire();
    sort();
    prelucare();
    return 0;
}
```