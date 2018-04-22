#Problema colorarii unei tari

Se dau n tari impreuna cu relatiile de vecinatate cu acestea
Coloreaza harta utilizand un nr minim de culori astfel incat sa nu existe 2 tari vecine colorate la fel

#####Date de intrare 
```
n
1 2
1 3
2 3
2 4
2 5
2 6
3 4
4 5
4 7
5 6
5 7
6 7

```
```C++
int a[100][100], n, sol[100], nrColors=1;

void citire(){
	freopen("date.in", "r", stdin);
	cin>>n;
	int x, y;
	while(cin>>x>>y){
		a[x][y]=a[y][x]=1;
	}
}

void colorTheShit(){
	sol[1]=1;
	for(int i=2; i<=n; i++){
		int c=1;
		do{
			bool ok=true;
			for(int j=1; j<=n; j++){
				if(a[i][j] && sol[j]==c){
					ok=false;
					breack;
				}
			}
			if(ok==false){
				c++;
			}
		}while(!ok);
		sol[i]=c;
		if(c>nrColors){
			nrColors = c;
		}
	}
}

void afisare(){
	for(int i=1; i<=n; i++){
		cout<<"pentru tara "<<i<<" avem culoarea "<<sol[i]<<endl;
	}
}

```
