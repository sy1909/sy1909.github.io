---
layout: post
title: "1/10 practice test code"
img: c++image.png # Add image post (optional)
date: 2018-01-10 18:57:00 +0900
description: You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. # Add post description (optional)
tag: [Programming]
---
//10951번 입력케이스가 주어지지 않은 반복
/*
#include <iostream>
using namespace std;

int main(){
	int a,b;
	while(cin>>a>>b){ //입력 받을 테스트의 수가 주어지지 않은경우 사용
		cout<<a+b<<endl;

	}
	return 0;
}
*/


/*
//11718번 입력 받은 대로 출력하는 프로그램
#include <iostream>
#include <string>
using namespace std;

int main(){
	string a;
	while(1){
		getline(cin, a);

		if(a =="")
			break;
		cout<<a<<endl;
	}
	return 0;
}
//getline을 쓰는것이 핵심  getline( 입력객체(cin, ifstream 객체 등), string 변수 ) : 공백을 포함하여 개행까지의 내용을 입력받을 수 있다!
*/
/*
//11719번 
#include <iostream>
using namespace std;

int main(){
	string a;
	for(int i=0; i<100; i++){
		getline(cin, a);
		//입출력 알고리즘
		cout<<a<<endl;

	}
	return 0;
}
*/
/*
//11720 char를 int로 바꾸어 숫자계산 아마 0-9까지만 가능할 듯
#include <iostream>
#include <string>
using namespace std;

int main(){
	int sum = 0, a;
	char c[100];
	cin >> a;		

	for(int i=0; i<a; i++){
		cin >> c[i];
		sum += (c[i]-'0');
	}
	cout<<sum<<endl;
	return 0;
}
*/

/*
//11723번 집합 bit연산과 strcmp , switch를 사용해도 괜찮았을 듯 함
// 시간초과에 유의하자 비트마스크 연산에서 b--를 해주지 않으면 해당 비트값을 제대로 비교하지 못한다.
#include <iostream>
#include <cstring>
using namespace std;

int main(){ //cin, cout은 시간이 너무 오래걸린다.
	char t[10];
	int a,b, bit;
	scanf("%d", &a);

	for(int i=0; i<a; i++ ){
		scanf("%s", t);
		if(!strcmp(t, "add")){ // strcmp의 반횐값은 같을 경우 0이다.
			scanf("%d", &b);b--;
			bit = bit | (1<< b);
		}
		else if(!strcmp(t, "remove")){
			scanf("%d", &b);b--;
			bit = bit & ~(1<<b);
		}
		else if(!strcmp(t, "check")){
			scanf("%d", &b);b--;
			if(bit&(1<<b)){
				printf("%d\n", 1);
			}
			else
				printf("%d\n", 0);
		}
		else if(!strcmp(t, "toggle")){
			scanf("%d", &b);b--;
			bit = (bit^(1<<b));
		}
		else if(!strcmp(t, "all")){
			bit = (1<<21)-1;
		}
		else if(!strcmp(t, "empty")){
			bit = 0;
		}
	}
	return 0;
}
*/

/*
깊이 우선 탐색 (Depth First Search)
현재 정점에 연결된 정점이 존재하면 계속 이동한다.
방문한 정점을 재귀호출을 이용해서 스택에 저장한다.
재귀호출을 이용하면 할수록 깊은 정점의 위치에 들어간다.
너무 깊게 들어가면 overflow 발생한다.
막히면 나아갈 곳이 있는 곳으로 돌아간다 -> 백트래킹
유용 : 사이클 탐지(Cycle Detection), 위상 정렬(Topological Sorting)
장점 : 무한히 넓은 트리에 효과적이다.
단점 : 목표 노드가 없는 경로에 깊이 빠질 수 있다.

너비 우선 탐색 (Breadth First Search)
생성된 순서에 따라 노드를 확장한다.
시작 정점을 출발로 큐 구조에 방문한 정점을 넣어가며 탐색을 한다.
한 정점에 연결된 모든 정점의 탐색이 끝나면 그 정점을 큐에서 제가한다.
그리고 큐의 다음 정점을 꺼내서 그 정점에 연결된 모든 정점을 탐색한다.
많은 기억 공간이 필요하다.
유용 : 최소신장트리(Minimum Spanning Trees), 최단경로(Shortest Paths)
장점 : 무한히 깊거나 무한에 가까운 트리인 경우에 효과적이다.
단점 : 목표 노드로 가는 경로들 모두가 같은 거리일 때 비효율적이다.
[출처] 깊이우선탐색 너비우선탐색 차이점 DFS vs BFS|작성자 숨은보물
ihope9483@gmail.com
*/

/*
//10972번 문제 순열 알고리즘 사용 next_permutation 함수를 사용해도 가능하다.
//누가 stl의 내장 알고리즘을 더 잘 알고있느냐가 문제해결의 관건이 되기도 한다.
//stl을 공부할 필요성을 느낀다. 아주 효율적인 프로그래밍 도구!
#include <iostream>
#include <algorithm>
using namespace std;

int main(){
	int n;
	cin >> n;
	int arr[10001];
	int tmp[10001];

	for(int i=0; i<n;i++){
		cin >> arr[i];
		tmp[i] = arr[i];
	}

	//stl 두가지
	sort(tmp, tmp+n);
	next_permutation(arr, arr+n);
	
	bool chk = true;
	
	for(int i = 0; i<n; i++){
		if(tmp[i]!=arr[i]){
			chk = false;
			break;
		}
	}
	if(!chk){
		for(int i = 0; i< n; i++){
			cout << arr[i] << " ";
		}
	}
	else
		cout << -1<<endl;

	return 0;
}
*/

/*
//10973번의 문제 사전순 알고리즘의 바로 전 순열을 출력한다. prev_permutation을 이용 (stl)
#include <iostream>
#include <algorithm>
using namespace std;

int main(){
	int n;
	cin >> n;
	int arr[10001];
	int tmp[10001];

	for(int i=0; i<n;i++){
		cin >> arr[i];
		tmp[i] = arr[i];
	}

	
	sort(tmp, tmp+n);

	bool chk = true;
	for(int i = 0; i<n; i++){
		if(tmp[i]!=arr[i]){
			chk = false;
			break;
		}
	}
	if(!chk){
		prev_permutation(arr, arr + n);
		for(int i = 0; i< n; i++){
			cout << arr[i] << " ";
		}
	}
	else
		cout << -1<<endl;

	return 0;
}
*/

/*
//10974번 next_permutation과 prev_permutation의 순열 stl활용을 알아볼 수 있는 문제들 이었다.
#include <iostream>
#include <algorithm>
#include <cstdio>
using namespace std;

int main()
{
    int p[] = {1, 2, 3, 4, 5, 6, 7, 8};
    int n;

    scanf("%d", &n);

    do {
        for (int i = 0; i < n; i++)
            printf("%d ", p[i]);

        printf("\n");
    } while (next_permutation(p, p + n));

    return 0;
}
*/



//1722 나중에 해보기 머리 아프다. 



//1476번 날짜계산 








