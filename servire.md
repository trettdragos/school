#Timp minim de servire

Un restaurant satisface cererile a n clientii. Pentru fiecare client se cunoaste timpul de servire. Se cere sa se minimizeze timpul total de servire a acelor n clienti

####Exemplu

n=3
T=(7, 3, 5)

Timpul de asteptare al clientului i: T1+T2++...+Ti

Ordinea 1 2 3 => 7 + (7+3) + (7+3+5)=32
132 => 7+(7+5)+(7+5+3)=34

Timp minim: 2, 3, 1 =>3+(3+5)+(3+5+7)=26

```c++
int n
struct client{
	int nr, timp;
}a[100];

void citire(){
	ifstream f("date.in");
	f>>n;
	for(int i=1; i<=n; i++){
		f>>a[i].nr>>a[i].timp;
	}
}

void sort(){
	for(int i=1; i<n; i++){
		for(int j=i+1; j<=n; j++){
			if(a[i].timp<a[j].timp){
				client auxiliar = a[i];
				a[i]=a[j];
				a[j]=auxiliar;
			}
		}
	}
}

void preluc(){
	int totalTime = 0;
	int timeClienti = 0;
	for(int i=1; i<=n; i++){
		timpClinti=ti+a[i].timp;
		timpTotal+=timpClienti;
		cout<<a[i].nr;
		cout<<endl;
		cout<<"Timp total "<<timpTotal;
	}
}

int main(){
	citire();
	sort();
	preluc();
}

```