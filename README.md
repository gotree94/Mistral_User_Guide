# Mistral Large 4 (Le Chonk, mistralai/Mistral-Large-4-1T-A52B) — 다운로드 & 팩트체크

> 다른 PC에서 다운로드받기 위한 최종 정리 문서
> - 모델: https://huggingface.co/mistralai/Mistral-Large-4-1T-A52B
> - 참고 영상: https://youtu.be/Zim5W1nTbJ0
> - 가중치 공개일: 2026-10-29 (Hugging Face)
> - 최종 업데이트: 2026-11-05

**한 줄 요약:** 승인 없이 누구나 무료로 받을 수 있지만 **약 1,060GB(1.04TB)**이고, 가장 작은 압축판도 약 **233GB**라 **일반 노트북(16GB)에서는 실행 불가**입니다. "세계 최초 1조 공개 모델"도 아닙니다.

---

## 0. 한눈에 보기

| 항목 | 내용 |
|---|---|
| 별명 | **Le Chonk** (뚱뚱한 고양이 밈) |
| 받는 비용 | 무료 (승인 절차 없음) |
| 다운로드 크기 | 약 **1,060.6 GB** (약 1.04TB) |
| Safetensors 샤드 | **54개** (`consolidated-00001-of-00054` ~ `00054`), 전체 파일 약 68개 |
| 총 파라미터 | 약 **1조 (1T)** |
| 활성 파라미터 | 약 **52B** (임베딩/출력 포함, 본체 49B) |
| 컨텍스트 | 1,048,576 토큰 (약 100만) |
| 입력 | 텍스트 + 이미지 (멀티모달) |
| 일반 PC/노트북 실행 | ❌ 불가 (최소 압축판 약 233GB) |
| 서버 실행 | ✅ 8×B200급(또는 8×MI300X/MI355X급) 텐서 병렬 8 |
| 라이선스 | Mistral Ecosystem Open-Weight License (수정 MIT, MaaS 사업은 별도 계약) |
| API | ✅ Mistral API (`mistral-large-4`) |

---

## 1. 팩트체크 요약 (참고 영상 기준)

| # | 퍼진 말 | 판정 | 한 줄 근거 |
|---|---|---|---|
| 1 | "1조짜리 AI를 공짜로 풀었다" | **대체로 사실** | 다운로드는 무료·승인 불필요. 단 '서비스형 모델(MaaS)' 사업은 별도 상업 라이선스 |
| 2 | "세계 최초 1조 공개 모델" | **거짓** | 2025-07-11 문샷 AI **Kimi K2**(총 1조·활성 32B)가 이미 공개됨 |
| 3 | "내 노트북에서 돌린다" | **거짓** | 가장 작은 압축판도 약 **233GB**, 흔한 노트북 메모리 16GB |
| 4 | "해킹 AI를 풀었다" | **거짓** | 공개판은 악성 요청 거절률 **96.6%**로 발표. 공격 연구용 특화판은 심사 거친 기업에만 |
| 5 | "오픈 모델 1등" | **과장** | 코딩은 1위 주장 가능. 종합 지수는 **중국 오픈 모델이 더 높다**고 모델 카드에 명시 |

### 1.1 "1조짜리 AI를 공짜로 풀었다" — 대체로 사실
- 2026-10-29 Hugging Face에 가중치 공개, **승인 없이 누구나 다운로드** 가능.
- 단, 라이선스는 **Mistral Ecosystem Open-Weight License**(수정 MIT)로, 상업·비상업 사용은 허용되지만 **"Model-as-a-Service" 사업을 하려면 Mistral과 별도 상업 라이선스 계약**이 필요.
- → "받는 건 무료"는 사실, "아무 제약 없이 큰 장사도 가능"은 아님.

### 1.2 "세계 최초" — 거짓
- 2025-07-11 공개된 **Kimi K2**가 이미 총 1조 파라미터(활성 32B) 오픈 모델.
- 따라서 Mistral Large 4가 "세계 최초 1조 공개 모델"은 아님.

### 1.3 "내 노트북에서 돌린다" — 거짓
- 원본 가중치 약 1,060GB.
- Unsloth 등 **최소 압축(GGUF/1-bit 계열)판도 약 233GB**.
- 흔한 노트북 메모리 16GB로는 불가. 고사양 워크스테이션(수백 GB 메모리)에서도 매우 제한적.

### 1.4 "해킹 AI를 풀었다" — 거짓
- Mistral은 공개판이 **악성 요청을 거절**하도록 정렬되어 있으며, 발표 기준 거절률 **96.6%**.
- 사이버보안 **공격 연구용 특화판**은 아무나 받는 것이 아니라 **심사를 거친 기업/기관에만** 제공.
- → "해킹 도구가 무제한 풀렸다"는 오해.

### 1.5 "오픈 모델 1등" — 과장
- 모델 카드 기준 Artificial Analysis **Coding Agent Index 48%**로 GLM-5.3과 사실상 동률(토큰은 47% 적게 사용).
- Artificial Analysis **Intelligence Index v5 = 26**으로 **서구 오픈 모델 중 최고**이지만, **종합 지수는 중국 오픈 모델이 더 높다**고 카드에 직접 명시.
- → "코딩/사이버보안은 최상위권", "종합 1등"은 아님.

---

## 2. 모델 개요 (스펙)

| 항목 | 내용 |
|---|---|
| 개발사 | Mistral AI (프랑스) |
| 아키텍처 | Mixture-of-Experts (MoE), 네이티브 멀티모달 |
| 총 파라미터 | 약 1조 (1T) |
| 활성 파라미터 | 약 52B (임베딩/출력 포함) / 본체 49B |
| 전문가 구성 | 라우팅 전문가 128개(토큰당 4개 활성) + 공유 전문가 1개 |
| 컨텍스트 길이 | 1,048,576 토큰 (약 100만) |
| 입력/출력 | 텍스트 + 이미지 입력 / 텍스트 출력 (Pixtral 방식 비전 인코더) |
| 언어 | 160개 이상 (EU 공식 언어 전부 포함) |
| 추론 강도 | `low` / `medium` / `high` (기본 `high`) |
| 권장 샘플링 | `temperature=1.0`, `top_p=0.95` |
| 학습 인프라 | Mistral 유럽 자체 데이터센터, NVIDIA Grace Blackwell 3,800장 |
| 학습 | from scratch |
| 라이선스 | Mistral Ecosystem Open-Weight License |
| 양자화 변형 | NVFP4 체크포인트 별도 제공 (`Mistral-Large-4-1T-A52B-NVFP4`) |

---

## 3. 다운로드 용량 및 구성

- **총 다운로드 용량: 약 1,060.6 GB (≈ 1.04TB)**
- Safetensors 샤드 **54개** (`consolidated-00001-of-00054.safetensors` ~ `consolidated-00054-of-00054.safetensors`)
- 샤드 1개당 약 20GB (마지막 2개는 16.9GB / 4.2GB)
- 전체 파일 약 68개 (샤드 외 `config.json`, `params.json`, `tokenizer.json`, `tekken.json`, `chat_template.jinja`, `LICENSE`, `assets/`, `images/` 등)
- 승인 절차 없음(public)

> ⚠️ **주의**
> - 단일 디스크에 **1.5TB 이상 여유**를 권장합니다(다운로드 + 임시/캐시 고려).
> - 다운로드만 하고 실행하지 않을 경우, 이 문서의 **4~6번 항목만** 수행하면 됩니다.
> - 일반 PC(16~24GB VRAM/RAM)에서는 **실행 불가**합니다.
> - 경량 실행을 원하면 **NVFP4 체크포인트** 또는 Unsloth GGUF(최소 약 233GB)를 고려하세요.

---

## 4. 사전 준비

### 4.1 Python 및 huggingface_hub 설치

```bash
# Python 3.10 이상 권장
python --version

pip install -U "huggingface_hub[cli]" hf_transfer
```

- `hf_transfer`는 대용량 다운로드 속도를 크게 높여줍니다(권장).

### 4.2 (선택) Hugging Face 로그인

공개 모델이라 로그인 없이 받을 수 있지만, 속도 제한 회피를 위해 로그인 권장:

```bash
hf auth login
# 또는 구버전: huggingface-cli login
```

토큰 발급: https://huggingface.co/settings/tokens

### 4.3 다운로드 가속 활성화

Windows (PowerShell):

```powershell
$env:HF_HUB_ENABLE_HF_TRANSFER = "1"
```

Linux / macOS (bash):

```bash
export HF_HUB_ENABLE_HF_TRANSFER=1
```

---

## 5. 다운로드 명령

### 5.1 Windows (PowerShell)

```powershell
pip install -U "huggingface_hub[cli]" hf_transfer
$env:HF_HUB_ENABLE_HF_TRANSFER = "1"

hf download mistralai/Mistral-Large-4-1T-A52B --local-dir "D:\models\Mistral-Large-4"
```

### 5.2 Linux (bash)

```bash
pip install -U "huggingface_hub[cli]" hf_transfer
export HF_HUB_ENABLE_HF_TRANSFER=1

hf download mistralai/Mistral-Large-4-1T-A52B --local-dir /data/models/Mistral-Large-4
```

> 구버전 CLI를 쓰는 경우 `hf download` 대신 `huggingface-cli download`를 사용하세요.

### 5.3 더 작은 NVFP4 체크포인트 받기 (Blackwell GPU용)

```bash
hf download mistralai/Mistral-Large-4-1T-A52B-NVFP4 --local-dir /data/models/Mistral-Large-4-NVFP4
```

### 5.4 전체 용량이 부족할 때 (일부 파일만 받기)

예) config/토크나이저 + 1번 샤드만:

```bash
hf download mistralai/Mistral-Large-4-1T-A52B \
  --include "*.json" "*.jinja" "consolidated-00001-of-00054.safetensors" \
  --local-dir /data/models/Mistral-Large-4
```

---

## 6. 중단 후 재개 (Resume)

- `hf download`는 기본적으로 **이어받기(resume)** 를 지원합니다.
- 같은 `--local-dir`로 **동일한 명령을 다시 실행**하면 이미 받은 파일/부분은 건너뜁니다.

Linux:

```bash
until hf download mistralai/Mistral-Large-4-1T-A52B --local-dir /data/models/Mistral-Large-4; do
  echo "재시도..."; sleep 10
done
```

Windows (PowerShell):

```powershell
do {
  hf download mistralai/Mistral-Large-4-1T-A52B --local-dir "D:\models\Mistral-Large-4"
} while ($LASTEXITCODE -ne 0)
```

---

## 7. 다운로드 검증

### 7.1 파일 개수/용량 확인

Windows (PowerShell):

```powershell
$dir = "D:\models\Mistral-Large-4"
(Get-ChildItem -LiteralPath $dir -Filter "*.safetensors").Count   # 54 이어야 함
"{0:N1} GB" -f ((Get-ChildItem -LiteralPath $dir -Recurse | Measure-Object Length -Sum).Sum / 1GB)
```

Linux:

```bash
ls /data/models/Mistral-Large-4/*.safetensors | wc -l    # 54
du -sh /data/models/Mistral-Large-4                      # 약 1.04T
```

### 7.2 무결성 검증 (선택, 시간 소요)

```bash
hf download mistralai/Mistral-Large-4-1T-A52B --local-dir /data/models/Mistral-Large-4 --verify
```

> 수백 GB~1TB 읽기/해시 연산이 필요해 오래 걸립니다. 정상 완료 메시지가 떴다면 생략 가능.

---

## 8. (참고) 실행 — 서버급 장비에서만

이 모델은 일반 PC에서 실행 불가하며, **8-GPU 텐서 병렬** 서버가 필요합니다.

- vLLM(공식 권장): https://github.com/vllm-project/vllm (recipe: https://recipes.vllm.ai/mistralai/Mistral-Large-4-1T-A52B)
- SGLang: https://github.com/sgl-project/sglang (cookbook: https://docs.sglang.io/cookbook/autoregressive/Mistral/Mistral-Large-4)
- Transformers / llama.cpp / Unsloth(파인튜닝·GGUF)

vLLM 예시(8 GPU):

```bash
docker pull vllm/vllm-openai:mistral-large-4

docker run --runtime nvidia --gpus all \
  -v ~/.cache/huggingface:/root/.cache/huggingface \
  -p 8000:8000 \
  --ipc=host \
  vllm/vllm-openai:mistral-large-4 \
  --model mistralai/Mistral-Large-4-1T-A52B \
  --tensor-parallel-size 8 \
  --tool-call-parser mistral \
  --reasoning-parser mistral \
  --enable-auto-tool-choice \
  --gpu-memory-utilization 0.85
```

- `reasoning_effort`: `"low"` | `"medium"` | `"high"` (기본 `high`)
- 온도 `1.0`, `top_p 0.95` 권장
- 체크포인트에 **DSpark 추론(투기적 디코딩) 초안 헤드**가 포함되어 있어 `--speculative-config '{"method": "dspark", "num_speculative_tokens": 3}'` 로 최대 약 1.9배 처리량 향상 가능(하드웨어/워크로드 의존).

---

## 9. 다운로드 없이 쓰는 대안: API

로컬 다운로드/실행이 부담되면 Mistral API 사용을 권장합니다(모델 카드도 로컬 서빙이 느리면 API 권장).

- Mistral API 모델 ID: `mistral-large-4`
- 문서: https://docs.mistral.ai/models/mistral-large-4-0
- 공식 블로그: https://mistral.ai/news/mistral-large-4-oss/
- 데모 갤러리(출시 첫 주 소액 무료 예산): https://mistralai-ml4-le-chonk-gallery.hf.space/

---

## 10. 체크리스트

- [ ] 대상 PC 디스크 여유 공간 **1.5TB 이상** 확보
- [ ] Python 3.10+ 및 `huggingface_hub[cli]`, `hf_transfer` 설치
- [ ] (권장) `hf auth login` 완료
- [ ] `HF_HUB_ENABLE_HF_TRANSFER=1` 설정
- [ ] `hf download ... --local-dir <경로>` 실행
- [ ] safetensors 샤드 54개 / 약 1.04TB 확인
- [ ] (선택) `--verify`로 무결성 검증
- [ ] 실행하려면 8×B200급 서버인지 확인 (일반 PC 불가, 최소 압축판도 약 233GB)
- [ ] 상업적 서비스(MaaS)로 제공할 경우 별도 라이선스 필요 여부 확인

---

## 11. 출처

- 모델 카드: https://huggingface.co/mistralai/Mistral-Large-4-1T-A52B
- 파일 목록 API: https://huggingface.co/api/models/mistralai/Mistral-Large-4-1T-A52B/tree/main
- Mistral 공식 글(2026-10-29): https://mistral.ai/news/mistral-large-4-oss/
- Mistral Ecosystem Open-Weight License: https://huggingface.co/mistralai/Mistral-Large-4-1T-A52B/blob/main/LICENSE
- Hugging Face 블로그: https://huggingface.co/blog/mistral-large4
- NVFP4 체크포인트: https://huggingface.co/mistralai/Mistral-Large-4-1T-A52B-NVFP4
- Unsloth 실행 안내: https://unsloth.ai/docs/models/mistral-large-4
- Unsloth GGUF: https://huggingface.co/unsloth/Mistral-Large-4-1T-A52B-GGUF
- Kimi K2 모델 카드(2025-07-11, 총 1조·활성 32B): https://huggingface.co/moonshotai/Kimi-K2-Instruct
- TechCrunch(2026-10-29): https://techcrunch.com/2026/10/29/mistral-releases-weights-for-its-trillion-parameter-ai-model-targeting-cybersecurity/
- Decrypt(2026-10-06): https://decrypt.co/380192
- 참고 영상: https://youtu.be/Zim5W1nTbJ0
