#Arboti Binari - Aplicatii

Scriem o functie care sa determine inaltimea arborelui

```C++
int inaltime(nod *p){
	if(!p)
		return -1;
	int r1 = inaltime(p->st);
	int r2 = inaltime(p->dr);
	return (r1>r2?r1:r2)+1;
}
```

###Prb2

calc nr de val prime aflate pe fiecare nivel al arborelui

```C++
int nrp[100], n;
int prim(int x);

void valoriPrime(nod *p, int level){
	if(p){
		if(prim(p->inf)){
			nrp[nc]++;
		}
		n=nc>n?nc:n;
		valoriPrime(p->st, nc+1);
		valoriPrime(p->dr, nc+1);
	}
}

int main(){
	creareRadacina();
	valoriPrime(radacina, 0);
	for (int i = 0; i <= n; i++)
	{
		cout<<i<<": "<<nc[i]<<endl;
	}
	return 0;
}

```


##Prb3
Fisierrul date.in contine cuvinte separate printr-un spatiu. Acest fisier contine lista intr-o ordine a vf unui arbore binar in care absenta unui fiu este marcata de cuvantul '*'
Se cere: 
- construieste arborele binar asociat fiserului
- sa se afiseze nivelele care contin un nr maxim de cuvinte ce au literele in ordine alfabetica

```c++
struct nod{
	nod *st;
	nod *dr;
	char inf[31];
}*radacina

int a[100], levels;

ifstream f("date.in");

void creare(nod *&p){
	char x[31];
	f>>x;
	if(strcmp(x, "*") == 0){
		p = NULL;
	}else{
		p = new nod;
		strcpy(p->inf, x);
		creare(p->st);
		creare(p->dr);
	}
}

bool verif(char *s){
	for(int i=0; i<=strlen(s)-1; i++){
		if(s[i]>s[i+1]){
			return false;
		}
	}
	return true;
}

```