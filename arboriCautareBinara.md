#Arbori binari de cautare

Este un arbore binar in care oricare nod respecta urmatoarele proprietati:

- informatia utila asociata nodului x este >= decat orice informatie utila asociata nodurilor aflate in subarborele stang
- informatia utila asociata nodului x este <= decat orice informatie utila asociata nodurilor aflate in subarborele drept

Parcurgerea in inordine a unui arbore binar ne furnizeaza datele in ordine crescatoare

###Crearea unui arbore

#Teza

- prb eficienta variante
- prb arbori

##Prb

SA se creeeze un ABC in care informatia utila usnt nr intregi cititte dintr-un fisier

```c++
struct nod{
	int inf;
	nod *st, *dr;
}*rad;

void inserare(nod *&r, int x){//insereaza x in ABC de radacina r
	if(r==NULL){
		r= new nod;
		r->inf = x;
		r->st = NULL;
		r->dr = NULL;
	}
	else if(r->inf >= x){
		inserare(r->st, x);
	}else{
		inserare(r->dr, x);
	}
}

void creareArbore(nod *&r){
	ifstream f("date.in");
	int x;
	while(cin>>x){
		inserare(r, x);
	}
}

void main(){
	creareArbore(rad);
	inordine(rad);//pt parcurgere
	return 0;
}
```

##Parcurgerea inordine

```c++
void inordine(nod *r){
	if(r){
		inordine(r->st);
		cout<<r->inf<<" ";
		inordine(r->dr);
	}
}
```