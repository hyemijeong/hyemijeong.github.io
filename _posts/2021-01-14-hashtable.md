---
layout: post
title: "Hashtable"
date: 2021-01-14
excerpt: "연구선행학습2- c언어를 이용한 hashtable구현하기"
comments: true
---

앞의 포스트에서 liked list에 대하여 설명이 되었을것이다. hashtable은 무한의 데이터의 영역을 제한된 영역으로 표현하여 data를 저장할 수 있도록한다.


hashtable에서는 무한의 데이터를 key라고 하는데 hashFuction을 통해 key를 유한한 데이터(hash)로 바꾸어 저장하여준다. 

예를 들어 아래와 같은 hash 가 0~9 까지의 유한한 데이터를 가질 수 있도록 짜여진 hashFuction 이라면
'''
void hashFunc (int key){
    int hash = key%10; //key값을 10으로 나눈 나머지
    return hasy;
}
'''

key값이 211,301,121, 이라면 이 key값에 대한 hash값은 모두 1이 될것이다.


이런식으로 무한한 값을 유한한 값으로 표현하여 저장하는 것이 hashtable이다.

