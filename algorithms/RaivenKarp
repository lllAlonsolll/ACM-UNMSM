#include <iostream>
#include <cstring>
#include <cstdio>
#define d 256                  // The dictionary of 256 characters
using namespace std;

int mod(int a, int b){
	return (a%b + b)%b;
}

void search(string text, string pat , int q){
	int n = text.size();
	int m = pat.size();
	int hash_text = 0, hash_pat = 0;
	int BASE = 1;                       
 
	for(int i=0;i<m-1;i++){
		BASE = mod(d*BASE,q); //Calculate Base Value mod q, d^(m-1) value
	}
 
	for(int i=0;i<m;i++){
		hash_pat = mod((d*hash_pat + pat[i]),q);
		hash_text = mod((d*hash_text + text[i]),q);
	}
 
	for(int i=0;i<=n-m;i++){
		if(hash_text == hash_pat){
			int j = 0;
			for(j=0;j<m;j++){
				if(text[i+j]!=pat[j])break;
			}
			if(j==m) cout<<"Pattern matched at index "<<i<<endl;
		} 
		if(i<n-m){
			hash_text = mod((d*(hash_text - text[i]*BASE) + text[i+m]),q);
			if(hash_text < 0) hash_text += q; 
		}
	}
}
 
int main(){
	string a,b;
	cout<<"Enter the text: "<<endl;
	cin>>a;
	cout<<"Enter the sub-string: "<<endl;
	cin>>b;
	int q=7;                      // Let the prime number for computation be 7
	search(a,b,q);  
	return 0;
}
