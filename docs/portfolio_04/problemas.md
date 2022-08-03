# Apresentação de Problemas relacionados

<p style="text-indent: 20px; text-align: justify">
Um dos problemas discutidos nesse tópico é o famoso n-Queen, que consiste em posicionar N rainhas em um tabuleiro de xadrez com tamanho NxN, o algoritmo abaixo utiliza da técnina backtracking, com algumas otimizações específicas, para contar a quantidade de maneiras distintas de resolver esse problema.
</p>

```c++
#include <bits/stdc++.h>

using namespace std;

int isValidSolution(int x, vector<int> &diagonal_principal,
            vector<int> &diagonal_secundaria,
            vector<int> &tabuleiro){

  int ret = 1;

  // Como já foi garantido que as rainhas estão em linhas
  //e colunas diferentes resta apenas validar as diagonais
  for(int i=0;i<x;++i){
    ret &= (diagonal_secundaria[i + tabuleiro[i]] == 1 &&
    diagonal_principal[i + (x - 1) - tabuleiro[i]] == 1);
  }

  // Caso não haja mais de uma rainha em nenhuma das diagonais
  // os posicionamentos estão validos e o retorno será 1, caso contrário 0.
  return ret;
}


int nQueen(int n, vector<int> &diagonal_principal,
            vector<int> &diagonal_secundaria,
            vector<int> &tabuleiro,
            list<int> &posicoes_disponiveis){

  if(n == 0){ // quando essa condição é satisfeita significa que todas
  //  as N rainhas foram posicionadas de alguma forma

    // Checa se a solução obtida é valida
    return isValidSolution((int)tabuleiro.size(),
    diagonal_principal, diagonal_secundaria, tabuleiro);

  }

  int ans = 0;

  for(int i=0;i<n;++i){

    int k = tabuleiro.size();

    // Posiciona a rainha em uma das colunas disponíveis
    tabuleiro[n - 1] = posicoes_disponiveis.back();

    // Retira essa posição da lista para que as próximas
    // não sejam posicionadas na mesma coluna
    posicoes_disponiveis.pop_back();

    // Aumenta a quantidade de rainhas nas diagonais
    ++diagonal_principal[(n - 1) + (k - 1) - tabuleiro[n - 1]];
    ++diagonal_secundaria[(n - 1) + tabuleiro[n - 1]];

    // Tenta posicionar as n-1 restantes
    ans += nQueen(n-1, diagonal_principal,
                  diagonal_secundaria,
                  tabuleiro,
                  posicoes_disponiveis);

    // Coloca a posição que foi adicionada de volta no começo da lista,
    // para que ela esteja disponível mas não seja repetida pela rainha atual
    posicoes_disponiveis.push_front(tabuleiro[n - 1]);

    // Remove a contagem de rainhas nessas diagonais
    --diagonal_principal[(n - 1) + (k - 1) - tabuleiro[n - 1]];
    --diagonal_secundaria[(n - 1) + tabuleiro[n - 1]];
  }

  return ans;

}

int main() {

  // Declaração e leitura do tamanho do tabuleiro e,
  // logo, quantidade de rainhas
  int N;
  cin >> N;

  // Para verificar quantas rainhas estão posicionadas nas diagonais
  // principais e secundária do tabuleiro
  vector<int> diagonal_principal(2*N, 0), diagonal_secundaria(2*N, 0);

  // Como as rainhas não podem se atacar, já a posicionaremos em linhas e
  // colunas distintas, isso será representado no vector tabuleiro
  // da seguinte forma: tabuleiro[i] = x, onde i = linha em que a rainha está
  // e x = coluna em que a rainha está
  vector<int> tabuleiro(N);
  list<int> posicoes_disponiveis;
  for(int i=0;i<N;++i){
    posicoes_disponiveis.push_back(i);
  }

  cout << nQueen(N, diagonal_principal,
                  diagonal_secundaria,
                  tabuleiro,
                  posicoes_disponiveis)
                  << endl;

  return 0;
}
```
