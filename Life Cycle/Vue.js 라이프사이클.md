# Vue.js 라이프 사이클



## 0. 정리

- 크게 정리하면 4가지로 나뉜다.
  1. Creation
  2. Mounting
  3. Updating
  4. Destruction



## 1.  라이프사이클 다이어그램

![vue.js life cycle](https://kr.vuejs.org/images/lifecycle.png)

### 1. Creation: 컴포넌트 초기화 단계

Creation 단계에서 실행되는 훅들이 라이프 사이클 중에서 가장 처음 실행된다.

이 단계는 컴포넌트가 돔에 추가되기 전이다. 서버 렌더링에서도 지원되는 훅이다.

따라서 클라이언트 단과 서버단 렌더링 모두에서 처리해야 할 일이 있으면 이단계에서 하면된다. 

돔이 추가되기 전이라 돔에 접근하거나 this.$el를 사용할 수 없다.

- beforeCreate
- created
  - data와 events가 활성화 되어 접근 할 수 있다. 여전히 템플릿과 가상돔은 마운트 및 렌더링이 되지 않은상태이다.



### 2. Mounting: 돔 삽입단계

Mounting 단계는 초기 렌더링 직전에 컴포넌트에 직접 접근할 수 있다.

서버 렌더링에서는 지원하지 않는다.

컴포넌트 초기에 세팅되어야 할 data fetch는 created 단계를 사용하는 것이 낫다.

- beforeMount
- mounted

※ 주의할 점

- 부모와 자식관계의 컴포넌트에서 생각한 순서대로 mounted가 발생하지는 않는다. 부모 mounted가 끝나고 자식 mounted가 실행되는 것이 아니라, 오히려 자식 mounted 훅이 끝날 때 까지 기다렸다가 실행된다.



### 3. Updating: Diff 및 재 렌더링 단계

컴포넌트에서 사용되는 반응형 속성들이 변경되거나 어떤 이유로 재 렌더링이 발생하게 되면 실행된다.



### 4. Destruction: 해체 단계