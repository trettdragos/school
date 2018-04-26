<span alt="date" style="float: right; font-style: italic; font-size: 14pt">17.04.2018</span>
<p style="text-align: center; font-size: 32pt">Problema Comis Voiajorului</p>
Se dau N orașe împreună cu costul deplasării între anumite orașe. Un comis voiajor trebuie să își prezinte produsele în toate cele N orașe. Se cere să se identifice un traseu pe care să-l parcurgă comis voiajorul care să fie de cost minim și să treacă prin toate orașele o singură dată. Se știe că pleacă dintr-un oraș de start și trebuie să ajungă tot în orașul de start.
Traseul = ciclu elementar care trece prin toate vârfurile grafului = ciclu hamiltonian
Muchii: [1, 2, 10], [1, 3, 14], [1, 4, 2], [1, 5, 6], [2, 3, 12], [2, 4, 3], [3, 5, 9], [4, 5, 8]
Start = 1;
1, 4, 2, 3, 5, 1, Cost = 2 + 3 + 12 + 9 + 6 = 32

```cpp
#include <iostream>
#include <fstream>

using std::cin;
using std::cout;
using std::ifstream;

int a[100][100], n, start, solutie[100];
bool viz[100];

void citire() {
	ifstream in("date.in");
	in >> n >> start;
	int x, y, cost;
	while(in >> x >> y >> cost)
		a[x][y] = a[y][x] = cost;
}

void Greedy() {
	int costTotal = 0;
	int k = 1;
	int minim, vf;
	solutie[1] = start;
	viz[start] = true;
	while(k < n) {
		minim = 1000000;
		for(int i = 1; i <= n; i++) {
			if(a[sol[k]][i] < minim && a[sol[k]][i] && !viz[i]) {
				minim = a[sol[k]][i];
				vf = i;
			}
		}
		if(minim != 1000000) {
			sol[++k] = vf;
			viz[vf] = true;
			costTotal += minim;
		}else {
			cout << "Nu există soluție\n";
			return;
		}
	}
	if(a[sol[k]][start]) {
		costTotal += a[sol[k]][start];
		for(int i = 1; i <= k; i++) 
			cout << sol[i] << " ";
		cout << start << "\nCost total: " << costTotal;
	}else {
		cout << "Nu există soluție\n";
	}
}

int main() {
	return 0;
}
```