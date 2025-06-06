# Git Submodule 정리 (2025-06-06)

## 목적

* 학습용 레포지토리를 한 곳(`education_busan`)에 모아 정리
* GitHub 페이지가 너무 많아져 가독성 낮아진 점을 개선

## 적용 내용

* `education_busan`이라는 메인 레포지토리를 생성
* Git Submodule을 활용해 기존의 학습용 레포들을 폴더처럼 포함
* 다음 레포지토리들을 모두 서브모듈로 추가:

  * html, css, javascript, jquery, python, Java, Oracle, spring\_legacy, spring\_boot, etc...

## 사용 명령어

```bash
git submodule add <서브모듈 URL> <폴더명>
git submodule init
git submodule update
```

## 배운 점

* Git Submodule은 프로젝트 구조를 정리하면서도 개별 저장소의 독립성 유지 가능
* 향후 교육 프로젝트나 포트폴리오를 정리할 때 유용하게 활용 가능

## 참고

* `.gitmodules` 파일과 `.git/config`가 자동으로 생성됨
* 서브모듈을 클론받는 사람은 다음 명령어 사용 필요:

```bash
git clone --recurse-submodules <메인레포주소>
# 또는
cd education_busan
git submodule update --init --recursive
```
