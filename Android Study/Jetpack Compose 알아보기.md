# Compose란?
---
- Native UI를 Build하기 위한 Android의 최신 Tool Kit
- 적은 양의 코드, 강력한 도구, 직관적인 Kotlin API로 UI 개발 간소화하고, 가속화
- **선언적 접근 방식**으로, 데이터를 UI 계층 구조로 변환하는 함수를 호출하여 UI 생성
- 데이터가 변경되면, **함수를 재실행**하여 UI 계층 구조를 업데이트함

# Compose의 이점
---
## 코드 감소

- 테스트, 버그 작업, 버그 발생 가능성이 감소
- 코드를 읽고, 이해하고, 검토하고, 유지관리할 코드가 적음
- Android View 시스템보다 적은 코드로 더 많은 작업 가능

## 직관적

- **선언적 API 사용**을 통해 Compose가 나머지 처리를 맡아서 하므로 UI를 설명하기만 하면 됨
- 특정 활동이나 Fragment에 종속되지 않는 **Stateless 구성 요소**를 빌드하여 코드를 재사용하고, 테스트하기 쉬움
# Composable 함수
---
- **@Composable** annotation을 이용한 일반 함수이며, 다른 Composable 함수를 호출 가능
- Annotation은 지속적으로 UI를 업데이트하고, 유지관리하기 위해 함수에 특수 지원을 추가하도록 Compose에 알려주는 역할
- 새로운 UI 구성요소를 만들기 위해서는 Composable 함수만 만들어주면 됨


# 
---

# 참고 자료
---
1. [Android Compose 문서](https://developer.android.com/jetpack/compose?hl=ko)
2. [기존 App에 Compose 기능 추가](https://developer.android.com/jetpack/compose/setup?hl=ko)
3. [Material Design 3](https://m3.material.io/)

# Tutorial 참고
---
1. [Jetpack Compose 기초](https://developer.android.com/codelabs/jetpack-compose-basics?hl=ko&continue=https%3A%2F%2Fdeveloper.android.com%2Fcourses%2Fpathways%2Fjetpack-compose-for-android-developers-1%3Fhl%3Dko%23codelab-https%3A%2F%2Fdeveloper.android.com%2Fcodelabs%2Fjetpack-compose-basics#6)
2. 