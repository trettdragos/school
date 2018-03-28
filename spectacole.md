#Problema spectacolelor

Se dau:
- n spectacole cu nume si interval de desfasurare(hh:mm-hh:mm)
Se cere:
- planificarea unui nr maxim de spectacole intr-o zi astfel incat sa nu se suprapuna

####Exemplu
12:30-16:30 Primavara
15:00-18:00 Vara
10:00-18:30 Toamna
18:10-20:45 Iarna
12:15-13:00 Anotimpuri

####Rezolvare
- sortam credcator spectacolele dupa ora de terminare
- primul sp planif este cel care se termina mai repede
- parcurgem restul sp si planificam acele spectacole care au proprietatea ca ora la care incepe > ora la care se termina ultimul spectacol planificat

#####Afisare
12:15-13:00 Anotimpuri
12:30-16:30 Primavara
15:00-18:00 Vara
10:00-18:30 Toamna
18:10-20:45 Iarna


```c++
int n;
struct spectacol{
	char nume[20];
	int m1,m2;
}a[100];

void sortare(){
	for (int i = 0; i < n-1; i++)
	{
		for (int j = 0; j < n; j++)
		{
			if(a[i].m2>a[j].m2){
				specatcol aux = a[i];
				a[i]=a[j];
				a[j]=aux;
			}
		}
	}
}

void citire(){
	freopen("date.in", "r", stdin);
	cin>>n;
	int h1, m1, h2, m2;
	for (int i = 0; i < n; ++i)
	{
		cin>>h1>>m1>>h2>>m2;
		m1 = 60*h1 + m1;
		m2 = 60*h2 + m2;
		a[i].m1=m1;
		a[i].m2=m2;
		cin.geline(a[i].nume);
	}
}

void plan(){
	cout<<a[0].nume;
	int finisLast = a[0].m2;
	for (int i = 1; i < n; ++i)
	{
		if(a[i].m2>x){
			cout<<a[i].nume;
			finishLast=a[i].m2;
		}	
	}
}

```