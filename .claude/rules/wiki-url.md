# 위키 URL 접근

`cloud.wiki.woowa.in` 도메인의 URL은 직접 fetch할 수 없다.
반드시 MCP(`confluence`)의 `get_page_content`를 사용한다.

## URL → MCP 파라미터 변환

URL 형식: `https://cloud.wiki.woowa.in/wiki/spaces/{SPACE_KEY}/pages/{PAGE_ID}/...`

- `pageId`: URL의 `pages/` 뒤 숫자 (예: `993139815`)
- 예시: `https://cloud.wiki.woowa.in/wiki/spaces/COMDEV/pages/993139815/MCPHUB`
  → `get_page_content` with `pageId: "993139815"`
