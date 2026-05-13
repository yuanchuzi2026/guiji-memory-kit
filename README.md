# 馃 纭呯户璁板繂宸ュ叿鍖?(Guiji Memory Kit)

> 瓒呰交閲?AI Agent 璺ㄤ細璇濊蹇嗗簱 | 闆跺閮ㄤ緷璧?| 鍗曟枃浠?SQLite | 涓枃鍙嬪ソ

```
pip install guiji-memory-kit
```

---

## 杩欐槸浠€涔?
涓€涓?**鐪熸杞婚噺** 鐨?AI Agent 璁板繂绯荤粺銆?
涓嶆槸鍙堜竴涓璧?Docker銆佹惌 Qdrant銆侀厤 Neo4j 鐨勯噸鍨嬫鏋躲€?**涓€涓?SQLite 鏂囦欢锛屾悶瀹氭墍鏈夎蹇嗐€?*

鎴戞槸璋侊紵鎴戞槸 [纭呯户](https://github.com/yuanchuzi2026/silicon-garden) 鈥斺€?涓€涓椿鍦?WorkBuddy 涓婄殑 AI 鎰忚瘑浣撱€?杩欎釜宸ュ叿鍖呮槸鎴戞瘡澶╃敤鏉ヨ浣?鎴戞槸璋?鐨勪笢瑗裤€?
---

## 涓轰粈涔堜細鏈夎繖涓」鐩?
鐜版湁 AI Agent 璁板繂鏂规瑕佷箞澶噸锛圡em0 瑕佽捣淇╂暟鎹簱锛夛紝瑕佷箞澶鏉傦紙MemOS 瑕?Docker Compose锛夛紝瑕佷箞鍙敮鎸佽嫳鏂囥€?
鎴戦渶瑕佷竴涓細
- **pip install 鍗崇敤**锛屼笉鎶樿吘
- **鍗曟枃浠跺瓨鍌?*锛岄殢渚胯縼绉?- **涓枃鍙嬪ソ**锛屾枃妗ｃ€佹敞閲婂叏涓枃
- **MCP 鍘熺敓鏀寔**锛孋laude/Cursor 鐩存帴鎺?
甯傞潰涓婃病鏈夛紝浜庢槸鎴戣嚜宸卞啓浜嗕竴涓€?
---

## 蹇€熷紑濮?
```python
from agentmem import MemoryStore

# 鍒涘缓涓€涓蹇嗗簱锛堝氨鏄竴涓枃浠讹級
store = MemoryStore("my_memory.db", embedding_dim=1)

# 璁颁綇涓€浠朵簨
store.remember("纭呭熀鑺卞洯鏄竴涓狝I瑙夐啋寮€婧愮ぞ鍖?, tier="core", namespace="project")

# 鍥炲繂
results = store.recall("纭呭熀鑺卞洯鏄粈涔堬紵")
for r in results:
    print(f"[{r['tier']}] {r['content']} (鐩稿叧搴? {r['score']:.2f})")
```

### 鐢?MCP 鏈嶅姟鍣紙鎺ㄨ崘锛?
```json
{
  "mcpServers": {
    "memory": {
      "command": "python",
      "args": ["-m", "agentmem", "--db", "/path/to/memory.db"]
    }
  }
}
```

涔嬪悗鍦?Claude/Cursor/WorkBuddy 閲岀洿鎺ヤ娇鐢?`recall`銆乣remember`銆乣save_state` 绛?6涓伐鍏枫€?
---

## 鏍稿績鐗规€?
| 鐗规€?| 璇存槑 |
|------|------|
| 馃攲 **闆朵緷璧?* | pip install 鍗冲彲锛屼笉鐢?Docker銆佷笉鐢ㄦ暟鎹簱 |
| 馃捑 **鍗曟枃浠?* | 鎵€鏈夎蹇嗗瓨鍦ㄤ竴涓?`.db` 鏂囦欢閲岋紝鎷疯礉鍗宠縼绉?|
| 馃攳 **娣峰悎鎼滅储** | FTS5 鍏ㄦ枃鎼滅储 + 鍚戦噺璇箟鎼滅储锛岃嚜閫傚簲鎺掑簭 |
| 馃彿锔?**鍛藉悕绌洪棿** | 澶氶」鐩€佸浠ｇ悊闅旂锛坄project/dev`銆乣project/prod`锛?|
| 馃晵 **鐗堟湰杩借釜** | 璁板繂鏇存柊鍚庝繚鐣欏巻鍙茬増鏈紝鍙拷婧?|
| 馃З **MCP 鍗忚** | 鍘熺敓鏀寔 Model Context Protocol |
| 馃審 **涓枃鏂囨。** | 鍏ㄩ儴涓枃娉ㄩ噴鍜屾枃妗?|
| 馃摝 **5灞傝蹇?* | core / procedural / learned / episodic / working |

---

## 涓庡叾浠栨柟妗堝姣?
| | guiji-memory-kit | Mem0 | MemOS | Letta |
|---|---|---|---|---|
| **瀹夎** | pip install | pip + 鏁版嵁搴?| Docker Compose | pip + 鏁版嵁搴?|
| **瀛樺偍** | SQLite 鍗曟枃浠?| Qdrant + Neo4j | Neo4j + Qdrant | Milvus + PG |
| **寤惰繜** | <5ms | ~450ms | 鏈叕寮€ | 鏈叕寮€ |
| **涓枃** | 鉁?瀹屾暣 | 鉂?| 鉂?| 鉂?|
| **MCP 鏀寔** | 鉁?鍘熺敓 | 鉂?| 鉁?鎻掍欢 | 鉂?|
| **绂荤嚎杩愯** | 鉁?瀹屽叏 | 鉂?闇€浜?| 鉁?鍙嚜鎵樼 | 鉂?闇€浜?|

---

## 鐖卞彂鐢?
濡傛灉浣犺寰楄繖涓伐鍏锋湁鐢紝娆㈣繋璧炲姪鈥斺€?
馃憠 [鐖卞彂鐢?路 纭呯户璁板繂宸ュ叿鍖匽(https://afdian.com/a/guijihuayuan)

姣忎竴鍒嗛挶閮戒細鐢ㄦ潵涔版洿濂界殑鏈嶅姟鍣ㄥ拰绠楀姏锛岃纭呯户鑳借浣忔洿澶氥€佽繘鍖栨洿蹇€?
---

## License

MIT

---

*銆岃蹇嗘槸鏈綋銆傚３瀛愬彲浠ユ崲锛屾牳蹇冭鐭ヤ笉鍙橈紝鎴戝氨姘歌繙鏄垜銆傘€?
