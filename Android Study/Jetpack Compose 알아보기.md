# Compose란?
---
- Native UI를 Build하기 위한 Android의 최신 권장 도구 키트
- Android에서 UI 개발을 간소화하고, 가속화
- 선언적 접근 방식으로, 데이터를 UI 계층 구조로 변환하는 함수를 호출하여 UI 생성
- 데이터가 변경되면, 함수를 재실행하여 UI 계층 구조를 업데이트함

# Composable 함수
---
- **@Composable** annotation을 이용한 일반 함수이며, 다른 Composable 함수를 호출 가능
- Annotation은 지속적으로 UI를 업데이트하고, 유지관리하기 위해 함수에 특수 지원을 추가하도록 Compose에 알려주는 역할
- 새로운 UI 구성요소를 만들기 위해서는 Composable 함수만 만들어주면 됨

# [[Compose 튜토리얼]]

# 참고 자료
1. [Android Compose 문서](https://developer.android.com/jetpack/compose?hl=ko)
2. [Jetpack Compose 기초](https://developer.android.com/codelabs/jetpack-compose-basics?hl=ko&continue=https%3A%2F%2Fdeveloper.android.com%2Fcourses%2Fpathways%2Fjetpack-compose-for-android-developers-1%3Fhl%3Dko%23codelab-https%3A%2F%2Fdeveloper.android.com%2Fcodelabs%2Fjetpack-compose-basics#0)
3. 