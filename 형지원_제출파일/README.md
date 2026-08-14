# 2026 AI보안 기술개발 개인정보반 기말평가(실기)

klue/bert-base 기반 NER 모델과 정규식 규칙을 결합해 개인정보/위협정보를 익명화하는 파이프라인입니다.

## 구성
- `anonymize.ipynb` : 전체 파이프라인 (모델 로드 → NER 예측 → 정규식 탐지 → 병합 → submission.json 생성)
- `submission.json` : 최종 익명화 결과
- `label.txt` : 실제 탐지된 NER 라벨 목록
- `evidence.png` : 실행 증빙 스크린샷

## 사용 모델
- klue/bert-base (naver-ner 데이터셋으로 파인튜닝, 자체 테스트 F1 0.8401)
- 모델 가중치 파일은 용량 문제로 리포지토리에 포함하지 않았습니다.

## 정규식 탐지 항목
- 연락처(휴대전화/지역번호), 이메일, CVE, IPv4 (유효 옥텟 범위 0~255만 탐지)

## 실행 방법
1. `model_klue/` 폴더에 학습된 체크포인트(`config.json`, `model.safetensors`) 배치
2. `pip install torch transformers seqeval`
3. `anonymize.ipynb`를 Cell 1부터 순서대로 실행
