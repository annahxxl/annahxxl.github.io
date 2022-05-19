---
layout: post
title: "[Github Actions] Waiting for a runner to pick up this job..."
categories: DevOps
tags: [Github Actions, CI/CD]
---

### 문제

현재 진행 중인 프로젝트에서 Github Actions를 이용해 CI/CD 파이프라인을 구축해 둔 상태이다.
그런데 현재까지 개발된 내용들을 배포하려고 워크플로우를 실행시키는 과정에서 아래와 같은 문구와 함께 Queued 상태에 몇 시간 동안이나 머물러 있었다.

> Waiting for a runner to pick up this job...

저번 배포에서 정상적으로 실행됐던지라 에러 로그도 없는 상태였다..<br>
찾아보니 자체 호스팅 러너가 Github에 연결되지 않은 경우 문제가 될 수 있다는 것을 발견했고, 직접 확인해 보니 현재 연결되어 있는 러너가 실제로 Offline 상태였다! Offline 상태에서 Active 상태가 되어야 Github에 연결되어 워크플로우가 실행될 것 같았다.<br>

### 해결

그래서 ec2 인스턴스에 접속해 러너 로그를 아래의 명령어로 확인해 보았고, 조회된 내용이다.

```bash
tail -f ./actions-runner/nohup.out
```

<img align="left" alt="스크린샷 2022-04-27 19 11 44" style="margin-bottom: 24px;" src="https://user-images.githubusercontent.com/76666857/165499700-17a62b70-3474-4685-aed8-372ce46ce35e.png">

위의 내역을 통해 러너가 업데이트 이후 자동적으로 Active 상태로 만들어주진 않는다는 것을 알았다.<br>
그래서 아래의 명령어를 통해 러너를 다시 백그라운드로 실행시켜 Active 상태로 만들어주었다.<br>

```bash
nohup ./actions-runner/run.sh &
```

<br><br>
결론적으로 runner 상태가 업데이트로 인한 Offline 상태가 되었을 때, 현재까지 찾은 해결 방법으로는 업데이트가 되고 나면 수동으로 러너를 실행시켜 주어야 한다는 것이다..🥲

추가적으로, 필요하다면 러너의 상태를 확인할 수 있는 API를 사용하여 러너의 상태가 Offline 상태가 되었을 때를 체크할 수 있을것 같다.

### 참고

- [https://github.community/t/worker-nodes-show-offline-in-github/133760](https://github.community/t/worker-nodes-show-offline-in-github/133760){:target="\_blank"}
