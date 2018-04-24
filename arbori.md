contine lista vf arborilor binari parcursi intr-o oirdine in care absenta unui fiu se marcheaza cu val 0
###Se cere:
a) creaza dinamic radborele binar
b) afisaza lista vf parcuse in preordine, inordine, postordine
c) suma val din arbore 
d) ce mai mare val din arbore
e) afis vf de un nivel dat k
f) inlatimea arborelui

#####date.in:
```10, 9, 8, 0, 0, 17, 19, 0, 0, 0, 29, 13, 0, 14, 0, 0, 18, 20, 0, 0, 0```

####Code

```cpp
struct nod{
	int inf;
	nod *st, *dr;
}*nod;

ifstream fin("date.in");
void creare(){
	int x;
	fin>>x;
	if(x){
		p=new nod;
		p->inf = x;
		creare(p->st);
		creare(p->dr);
	}
	else{
		p=NULL:
	}
}

void preordine(nod *p){
	if(p){
		cout<<p->inf<<" ";
		preordine(p->st);
		preordine(p->dr);
	}
}

void inordine(nod *p){
	if(p){
		inordine(p->st);
		cout<<p->inf<<" ";
		inordine(p->dr);
	}
}
void postordine(nod *p){
	if(p){
		postordine(p->st);
		postordine(p->dr);
		cout<<p->inf<<" ";
	}
}

int suma(nod *p){
	if(p){
		return p->inf+suma(p->st)+suma(p->dr);
	}else return 0;
}

int basicMax(int x, int y){
	if(x>y){
		return x;
	}else  return y;
}

int maxArbore(nod *p){
	if(p){
		return basicMax(p->inf, basicMax(maxArbore(p->st), maxArbore(p->dr)));
	}else return -9999999;
}

int k; //nivelul citit de la tastatura

void afisareNivelDat(nod *p, int level){//level = nivelul curent
	if(p){
		if(level==k){
			cout<<p->inf<<" ";
		}
		if(level<k){
			afisareNivelDat(p->st, level+1);
			afisareNivelDat(p->dr, level+1);
		}
	}
}

```