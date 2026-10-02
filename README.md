# dudu.github.io

브라우저에서 OpenAI API를 직접 호출하는 간단한 채팅 UI 실험입니다. 파일은 `index.html` 하나입니다.

## 동작

1. 입력창에 메시지를 쓰고 **전송**을 누르면 오른쪽 말풍선으로 표시합니다.
2. `openai` 라이브러리(Skypack CDN)로 `createCompletion`을 호출합니다 (`text-davinci-002`, `max_tokens: 256`).
3. 응답 텍스트를 왼쪽 말풍선으로 추가합니다.

## 알려진 이슈

- **API 키가 `index.html`에 평문으로 커밋되어 공개 저장소에 노출되어 있습니다.** 이미 노출된 키이므로 OpenAI 대시보드에서 해당 키를 폐기(revoke)하고 새 키를 발급하세요. 키는 브라우저 코드에 넣지 말고 서버(예: [`zidududu.github.io`](https://github.com/zidudu/zidududu.github.io)의 `server.js` 방식)에서 환경변수로 관리해야 합니다. 커밋 이력에도 남아 있으므로 파일을 고쳐도 키 폐기는 필수입니다.
- `text-davinci-002`는 OpenAI에서 지원이 종료된 모델로 알려져 있어 호출이 실패할 수 있습니다.
- 입력값과 응답을 `insertAdjacentHTML`로 그대로 삽입합니다 (HTML 주입 위험).
- 대화 맥락을 유지하지 않고, 매 요청마다 현재 입력만 전송합니다.

## 실행

`index.html`을 브라우저로 열면 됩니다. 현재 키가 폐기되면 동작하지 않으므로 사용하려면 본인 키로 교체해야 합니다(위 보안 권고 참고).
