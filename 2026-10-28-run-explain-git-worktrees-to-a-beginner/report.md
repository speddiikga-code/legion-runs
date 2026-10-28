# Explain git worktrees to a beginner who runs several AI coding agents at once: what a worktree is, w

- Mode: run
- Date: 2026-10-28
- Limits: maxAgents 8, maxDepth 2, branching 3
- Stats: agents 2, splits 0, leaves 1, deepest 0, failed 0
- Tokens: 111,244

## Goal

Explain git worktrees to a beginner who runs several AI coding agents at once: what a worktree is, why each agent should get its own, and the exact commands to create, list and remove one. Under 250 words in total.

## Outline

```
1 Root [leaf]
```

## Result

**git worktree란**
repository 하나에 working directory를 여러 개 붙이는 기능이다. worktree마다 폴더, checkout된 branch, staging area(index)가 따로 있다. commit 기록과 object는 `.git` 하나를 같이 쓴다. 그래서 clone을 여러 번 하는 것보다 가볍고, 한 worktree에서 만든 commit을 다른 worktree에서 바로 볼 수 있다.

**agent마다 하나씩 줘야 하는 이유**
여러 agent가 같은 폴더에서 일하면 서로 고친 파일을 덮어쓴다. 한 agent가 `git checkout`이나 `git add`를 하면 다른 agent의 작업 상태도 바뀐다. agent마다 worktree를 주면 각자 자기 폴더와 branch에서 일하고, 결과는 branch 단위로 review한 뒤 merge하면 된다. 같은 branch를 두 worktree에서 동시에 checkout할 수는 없으므로 branch도 agent마다 따로 만든다.

**명령어** (repository 폴더 안에서 실행)

```
# main을 기준으로 branch agent-1을 새로 만들고 ../myrepo-agent-1 폴더에 checkout
git worktree add -b agent-1 ../myrepo-agent-1 main

# 모든 worktree와 각 worktree의 branch 보기
git worktree list

# 작업이 끝나면 worktree 제거 (commit하지 않은 변경이 있으면 거부됨)
git worktree remove ../myrepo-agent-1

# merge가 끝난 branch 삭제
git branch -d agent-1
```

**주의**
- 새 worktree에는 `node_modules`, `.venv` 같은 ignored 파일이 없으므로 dependency를 다시 설치해야 한다.
- 폴더를 직접 지웠다면 `git worktree prune`으로 남은 기록을 정리한다.

## Review

Complete: yes

- The create command assumes the base branch is called `main`. In a repo whose default branch is `master`, `git worktree add -b agent-1 ../myrepo-agent-1 main` fails with `fatal: invalid reference: main` (I checked this with git 2.55). A beginner needs a one-line note to replace `main` with their own base branch, or to leave it out so the new branch starts from the current HEAD.
- The comment on the remove command ('commit하지 않은 변경이 있으면 거부됨') doesn't make clear that new untracked files also block removal. Git's actual error is "contains modified or untracked files, use --force to delete it". It also never mentions `--force`, or that `--force` throws away that work.
- Some terms are never explained for a beginner: 'object', 'staging area(index)' and 'ignored 파일'. A few words of plain explanation would help, for example saying that ignored files are the ones listed in .gitignore.
- '서로 고친 파일을 덮어쓴다' overstates it. Agents sharing a folder *can* overwrite each other's files ('덮어쓸 수 있다'); it doesn't always happen.
- Optional, outside the stated goal: worktrees isolate only files, the index and HEAD. Stash, config and hooks are still shared, and so are runtime resources like ports and databases. Agents running dev servers or tests at the same time can still collide.
- Checked and fine: the text is about 100 whitespace-separated words, well under 250. I ran the add, list, remove (it refuses an unclean tree), branch -d and prune commands in a throwaway repo, and they behave as described. The claims about the shared .git and about not checking out the same branch in two worktrees are accurate.

## Every node

### 1 Root (leaf, depth 0)

**Task:** Explain git worktrees to a beginner who runs several AI coding agents at once: what a worktree is, why each agent should get its own, and the exact commands to create, list and remove one. Under 250 words in total.

**Why:** 설명 하나와 명령어 몇 줄이면 끝나는 250단어 미만 작업이라, 나누면 조율 비용만 늘어난다.

**git worktree란**
repository 하나에 working directory를 여러 개 붙이는 기능이다. worktree마다 폴더, checkout된 branch, staging area(index)가 따로 있다. commit 기록과 object는 `.git` 하나를 같이 쓴다. 그래서 clone을 여러 번 하는 것보다 가볍고, 한 worktree에서 만든 commit을 다른 worktree에서 바로 볼 수 있다.

**agent마다 하나씩 줘야 하는 이유**
여러 agent가 같은 폴더에서 일하면 서로 고친 파일을 덮어쓴다. 한 agent가 `git checkout`이나 `git add`를 하면 다른 agent의 작업 상태도 바뀐다. agent마다 worktree를 주면 각자 자기 폴더와 branch에서 일하고, 결과는 branch 단위로 review한 뒤 merge하면 된다. 같은 branch를 두 worktree에서 동시에 checkout할 수는 없으므로 branch도 agent마다 따로 만든다.

**명령어** (repository 폴더 안에서 실행)

```
# main을 기준으로 branch agent-1을 새로 만들고 ../myrepo-agent-1 폴더에 checkout
git worktree add -b agent-1 ../myrepo-agent-1 main

# 모든 worktree와 각 worktree의 branch 보기
git worktree list

# 작업이 끝나면 worktree 제거 (commit하지 않은 변경이 있으면 거부됨)
git worktree remove ../myrepo-agent-1

# merge가 끝난 branch 삭제
git branch -d agent-1
```

**주의**
- 새 worktree에는 `node_modules`, `.venv` 같은 ignored 파일이 없으므로 dependency를 다시 설치해야 한다.
- 폴더를 직접 지웠다면 `git worktree prune`으로 남은 기록을 정리한다.
