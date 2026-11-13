# 개요

본 저장소는 워너크라이(WannaCry)를 IDA로 정적 분석한 기록입니다.

## 분석 범위

제공받은 워너크라이 파일은 두 개의 exe 파일로 이루어져 있으며, 이 저장소는 그중 **mssecsvc.exe(전파·드로퍼 모듈)만** 다룹니다.

| 파일 | 역할 | 분석 여부 |
|---|---|---|
| [mssecsvc.exe](mssecsvc.exe/README.md) | 가장 먼저 실행되는 모듈. 킬 스위치 도메인 확인, 서비스 등록, tasksche.exe 추출·실행, SMB 취약점(MS17-010)을 이용한 자가 전파를 담당하는 Worm & Dropper | 분석 완료 |
| tasksche.exe | 파일 암호화를 수행하는 랜섬웨어 본체 | 분석하지 않음 |

mssecsvc.exe가 리소스에서 tasksche.exe를 꺼내 실행하는 지점([sub_407CE0](mssecsvc.exe/Pseudocode/sub_407CE0))까지 분석했으며, tasksche.exe의 암호화 로직은 이 저장소에서 다루지 않습니다.
