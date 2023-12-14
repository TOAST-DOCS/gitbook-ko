## Database > RDS for MS-SQL > 예약 작업

생성된 예약 작업을 확인, 수정, 삭제할 수 있습니다.

## 예약 작업

특정 작업을 원하는 시간에 시작할 수 있도록 예약 작업 기능을 제공합니다. 예약된 작업은 작업 예약 시간에 실행되지만, 작업 예약 시간 안에 완료되는 것을 보장하지는 않습니다.

### 예약 작업 상태

예약 작업의 상태 종류는 다음과 같습니다.

| 상태         | 설명                                      |
|------------|-----------------------------------------|
| 예약됨        | 작업 예약 시간이 되기 전 예약된 상태                   |
| 등록됨        | 작업 예약 시간이 되어 시작하기 전 상태                  |
| 진행 중       | 예약 작업 진행                                |
| 완료됨        | 예약 작업이 정상적으로 완료된 상태                     |
| 삭제됨        | 예약 작업이 삭제된 상태                          |
| 취소 요청 됨    | 예약 작업이 진행 중일 때 취소 요청됨                |
| 강제 취소 요청 됨 | 예약 작업이 진행 중일 때 강제 취소 요청됨             |
| 취소 중       | 예약 작업이 취소되어 취소에 필요한 작업이 진행되고 있는 상태     |
| 취소됨       | 정상적으로 취소된 상태                            |
| 오류         | 알 수 없는 이유로 예약 작업이 실패한 상태                |
| 검증 실패 | 예약 작업이 생성된 이후 DB 인스턴스가 변경되어 검증에 실패한 상태 |

### 예약 시간 타입

예약 작업 편집 시 선택할 수 있는 예약 시간 타입입니다.

| 예약 시간 타입 | 설명                               |
|----------|----------------------------------|
| 매일 반복    | 설정한 시간에 매일 반복해서 예약 작업 시작을 시도합니다. |
| 특정 시간 이후 | 특정 시간 이후 예약 작업을 시작합니다.            |