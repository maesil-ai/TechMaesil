---
title: Bye-bye! master 브랜치
---

Author: 김범규

우리는 git에서 `master` 브랜치를 삭제하기로 결심했다. 왜 그럴까?

## 배경

깃허브의 CEO인 Nat Friedman는 20년 6월 1일 노예제도와 관련된 용어인 `master` 를 대체 단어(main 등)로 [바꿀 것이라는 말](https://twitter.com/natfriedman/status/1271253144442253312)을 했다.

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">It&#39;s a great idea and we are already working on this! cc <a href="https://twitter.com/billygriffin22?ref_src=twsrc%5Etfw">@billygriffin22</a></p>&mdash; Nat Friedman (@natfriedman) <a href="https://twitter.com/natfriedman/status/1271253144442253312?ref_src=twsrc%5Etfw">June 12, 2020</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

받아들이는 사람에 따라 `master`, `slave`, `blacklist`와 같은 용어는 부적절한 의미를 함축할 수 있다고 느낄 수 있다.

또한 [2018년에 나온 저널](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6148600/)에서는 이런 말을 하기도 하였다.

> 이러한 용어는 인종 차별적 문화를 반영 할뿐만 아니라 이를 강화, 합법화 및 영속화하는 역할도 합니다. [name=Frank Houghton, Sharon Houghton]

또한 직관성의 이유도 있다. 블랙리스트/화이트리스트, 마스터/슬레이브는 그 용어를 처음 접했을 때 어떤 뜻인지 바로 알 수가 없다. 이미 익숙한 사람들은 무슨뜻인지 알겠지만 5살 아이에게 이게 무슨 뜻인지 설명하려고 한다면 아래에 있는 대체리스트에 있는 단어가 훨씬 직관적이라 생각한다.

당장은 기존 용어가 더 익숙하고 굳이 바꿔야할 이유를 모를수도 있다. 하지만 시간이 지나면 바뀐 용어가 더 익숙해질 것이라고 나는 확신한다.이미 이렇게 언어 순화가 이뤄지는 사례가 많이 있고 어떤 용어가 언어 순화가 이뤄진지 모르는 경우도 많다. 전산 용어 중에서도 대표적으로 '댓글'이 있다.

## 대체 리스트

### `master`

- `primary`
- `main`
- `default`
- `parent`
- `server`

### `slave`

- `secondary`
- `worker`
- `child`
- `helper`

### `blacklist`

- `denylist`
- `excludelist`
- `blocklist`

### `whitelist`

- `allowlist`
- `includelist`
- `throughlist`

## `master` 브랜치의 이름 바꾸기

실천이 가장 중요하다. 깃 브랜치의 이름을 바꾸는 것은 쉽다. 그런데 로컬과 업스트림을 동시에 바꾸거나, 브랜치가 디폴트 브랜치일때 조금더 까다로워진다.

그래도 어렵지 않으니 다들 한번씩 해보면 좋을것 같다.

### 브랜치 이름 바꾸는 방법

remote/upstream이 없을때는 그냥 `git branch -m master main`으로 할 수 있다.

1. 브랜치의 이름을 바꾸고 push 한다.

   ```shell
   git branch -m master main
   git push -u origin main
   ```

2. GitHub, GitLab과 같은 사이트에 들어가서 default branch를 조정한다.

3. master를 삭제하고 upstream remote의 HEAD를 업데이트한다.

   ```shell
   git push origin --delete master
   git remote set-head origin -a
   ```

### 이미 바뀐 브랜치 이름으로 바꾸는 법

공동으로 작업을 하고 있다면 다른 사람 역시 간단한 작업을 통해서 바꿔 줄 수 있다.

```shell
git fetch --all
git remote set-head origin -a
git branch --set-upstream-to origin/main
git branch -m master main
```

### 툴을 사용해서 바꾸는 법

[링크](https://eyqs.ca/tools/rename/)

브랜치 이름을 바꾸는 것과 관련된 툴이 존재한다. 간단한 클릭만으로 바꿀 수 있다.

## 결론

GitHub를 필두로 많은 회사, 단체들이 언어 순화를 진행하고 있고, Ruby, Python, Django, AWS 등 과 같은 곳들은 이미 내부에 쓰인 인종차별로 해석될 수 있는 단어를 전부 바꾼 상태이다.

GitHub도 업데이트가 이뤄지면 아마 `main`으로 바뀔 것으로 보이나 미리 자신의 브랜치 이름을 `main`으로 바꿔보는 것도 값진 경험일거라 나는 생각한다.

## 참조

[Git: Renaming the "master" branch](https://dev.to/rhymu8354/git-renaming-the-master-branch-137b)

[GitHub to replace "master" with alternative term to avoid slavery references
](https://www.zdnet.com/article/github-to-replace-master-with-alternative-term-to-avoid-slavery-references/)

---
