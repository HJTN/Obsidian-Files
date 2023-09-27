## Git 초기 설정
---
1. **git init** : 빈 Git 저장소 생성 -> .git 폴더 생성
2. **git config --global user.name "Github user name"**	// 처음 한 번만
3. **git config --global user.email "Github using email"**	// 처음 한 번만
4. **git status** : 생성, 수정, 삭제된 폴더들이 있는지 상태 확인
5. **git add -A 혹은 git add .** : 타임 캡슐에 저장
6. **git commit -m "변경 사항/ 내용 입력(설명)"** : 타임 캡슐을 묻음
7. **git log** : commit한 내용들 확인

## Log의 특정 시점으로 돌아가기
---
1. **git reset (돌아갈 시점의 commit한 내용의 6자리 글자) --hard** : 원하는 시점으로 되돌아감(특정 시점 이후에 commit한 내용 없어짐!)
❇️ **git push -f {원격명} {branch명}**: 로컬 branch의 돌아간 시점을 원격 레포의 branch에 적용
2. **git revert (취소할 시점의 commit한 내용의 6자리 글자)** : 원하는 시점으로 되돌아감(시점 이후가 지워지지 않음, 새 캡슐이 묻힘!)

## branch 설정
---
1. **git branch (branch이름)** : 평행우주 만듦
2. **git branch** : 생성된 branch 확인
3. **git branch -a** : remote/local의 branch 모두 확인
4. **git branch -M (branch이름)** : branch를 만들고 바로 만든 branch로 이동
5. **git checkout (원하는 branch)** : 특정 branch로 이동
6. **git branch -D (branch명)** : branch 삭제

## branch 병합
---
1. **git checkout (branch이름)** : merge할 branch로 이동
2. **git merge (변화를 가져올 branch이름)** : 현재 branch에 지정 branch를 병합
3. **git rebase (변화를 가져올 branch이름)** : 한 줄로 깔끔하게 정리(재배치)
❇️ **git log --graph --all --decorate** : 시각화된 작업 내역 확인

## Github
---
1. **git remote** : 현 폴더의 원격 레파지토리 확인
2. **git remote add (원격 저장소 이름) (repository url)** : 지정된 이름의 원격 저장소 생성
3. **git push -u (원격 저장소 이름) (branch명)** : github에 현재 폴더의 내용 업로드

## .gitignore(다루지 않을 파일 설정) 설정
---
1. .gitignore 파일에 올리지 않을 파일이름 작성

## 특정 Repository에서 파일 내려받기
---
1. **git clone (특정 레파지토리 url)** : 해당 url에 저장된 파일들 다운
2. **git fetch** : 변경된 사항들을 내려받음
3. **git status** : 변경된 사항 확인
4. **git pull (원격명) (브랜치명)** : 파일 다운

## 원격으로 branch 다루기
---
1. **git checkout -b (branch명)** : branch 생성 및 체크
2. **git push (원격명) (특정 branch명)** : github에 해당 branch 이름으로 파일 올림
3. **git checkout -b (branch명) (origin/branch명)** : 해당 branch 명에 origin/branch명에 있는 파일을 받아오고 넘어감
4. **git push -d (원격명) (브랜치명)** : 원격의 브랜치 삭제