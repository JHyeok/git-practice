### 1. 새로운 기능을 만들고 브랜치의 커밋 메시지를 합치고 수정하기

- feature 브랜치 생성한다.

`git checkout -b feature`

- feature 브랜치에서 두 개의 변경사항을 적용한 커밋을 추가한다.
- 전체의 기능을 부분적으로 쪼개서 커밋을 했다고 가정한다.

`git commit -m "2의 덧셈 기능 추가"`

`git commit -m "3의 덧셈 기능 추가"`

`git commit -m "다른 식의 덧셈 기능 추가"`

- feature 브랜치에서 위의 덧셈 기능을 하나의 커밋으로 합치려고 한다.
- pick을 squash로 변경해주면 되는데, pick과 squash를 설정하고 저장하고 나가면 커밋을 수정하는 창이 나온다.
- 3개의 커밋에서 b8914d1, e947fbd을 삭제하고 마지막 커밋에서 원하는 커밋 메시지로 변경한다.

`git rebase -i HEAD~3`

```
pick b8914d1 2의 덧셈 기능 추가
squash e947fbd 3의 덧셈 기능 추가
squash 4909524 다른 식의 덧셈 기능 추가
```

- 로그를 확인해본다.
`git log --pretty=oneline`

```
b14f9fb9018a241abf1e5e151943f911807cc976 (HEAD -> feature) 다른 식의 덧셈 기능을 추가합니다(git squash 연습)
c571caf9ad68582386b96fae18c32085e1c01e80 (origin/master, master) 영어 이름 추가
ff7964d6511e96bd5af87d38c0789be3f7bca138 Init
```

- 하지만 커밋 메시지가 마음에 들지 않아서 메시지를 변경하고 싶다.
`git commit --amend -m "다른 식의 덧셈 기능 추가" -m "Git Rebase와 Squash를 사용한 커밋 합치기 연습"`

- remote 저장소의 feature 브랜치에 push를 한다.
`git push -f -u origin feature`

- GitHub 플랫폼을 이용해서 feature 브랜치를 master 브랜치와 합친다.
`GitHub Compare and Pull Request`

- 직접 실습을 통해서 했는데 여러 시행착오가 있었다.
- push 하지 않은 커밋들에 대해서 squash 하는 것이 정신 건강에 이로울 것 같다.

### 2. Pull Request에서 Merge의 방법들

- Merge

![Merge](./image/merge.png)

- Squash and Merge

![Squash-And-Merge](./image/squash-and-merge.png)

- Rebase and Merge

- 참고 : https://meetup.toast.com/posts/122
