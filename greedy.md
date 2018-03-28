#Greedy

Metoda de elaborare a algoritmilor in care se cere solutia optima.

Alg pleaca de la o multime A si trebuie sa construiasca o submultime B al lui A care sa indeplineasca criteiile de optim. Constructia submultimii B se face astfel

- se pleaca de la multimea avida
- se iau pe rand elemente din A si se verifica daca din elementul curent adaugat la B conduce la solutia optima
- daca conduce atunci elementul este adaugat definitiv la B. Algoritmul nu se razgandeste asupra deciziei luate

####Exemplu 1

Se citeste o multime cu n numere reale, identificati o sublumtime a multimii date de suma maxima.

A={10, 7, -9, -4, 8, 2}
B={10, 7, 8, 2}

A={-10, -7, -9, -4, -8, -2}
B={-2}

```
int main(){
	int n, minim = -9999999, x, s;
	cin>>n;
	for(int i=0; i<n; i++){
		cin>>x;
		if(x>=0){
			cout<<x;
			s+=x;
		}else if(mimnim<x){
			minim=x;
		}
	}
	if(s)
		cout<<endl<<s;
	else cout<<minim;
}
```

####Exemplu 2

Se citesc 2 multimi cu elemente nenule.
A cu n elemente, B cu m elemente; n<=m
Sa se determine o submultime X al lui B care sa maximizeze valoarea expresiei ```a1*X1+a2*X2+.....+an*Xn```

A={9, 10, -8, -4}
B={2, 3, 11, 1, -8}
```
E2 = 9*2+10*3+(-8)*11+(-4)*1 = -44
E3 = 10*11+9*3+(-8)*(-8)+(-4)*1 = 110+27+64-4 = 137+60 = 197 
```
A crescator: A = {-8, -4, 9, 10}
B crescator: B = {-8, 1, 2, 3, 11}

```
int n, m, a[100], b[100];

void ordonare(int a[], int n){
	for(int i=0; i<n-1; i++)
	for(int j=i+1; j<n; j++){
		if(a[i]>a[j]){
			int aux = a[i];
			a[i]=a[j];
			a[j]=aux;
		}
	}
}

void expresie(){
	ordonare(a, n);
	ordonare(b. m);
	int e = 0;
	int i = 0;
	while(i<n && a[i]<0){
		e = e+a[i]*b[i];
		i++;
	}
	int j = n-1, k=m-1;
	while(j>=i){
		e = e+a[j]*b[k];
		j--;
		k--;
	}
	cout<<e;
}

int main(){
	citire();
	expresie();
}
```