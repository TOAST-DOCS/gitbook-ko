## Notification > KakaoTalk Bizmessage > Release Notes
### 2023. 11. 28.
* [API] 친구톡 와이드 이미지 버튼 개수 제한 변경
    * (변경 전) 친구톡 와이드 이미지 발송 시 최대 버튼 개수 1개
    * (변경 후) 친구톡 와이드 이미지 발송 시 최대 버튼 개수 2개

### 2023. 09. 26.
* [Console] 알림톡 채널 추가 시 안내되는 고정 문구 변경
    * (변경 전) 채널 추가하고 이 채널의 광고와 마케팅 메시지를 카카오톡으로 받기
    * (변경 후) 채널 추가하고 이 채널의 마케팅 메시지 등을 카카오톡으로 받기
* [Console] 본인 인증 반려 사유 노출
    * 본인 인증 탭에서 툴팁 형태로 반려 사유를 확인할 수 있도록 개선하였습니다.

### 2023. 08. 29.
* [API] 메시지 발송 결과 코드 업데이트 웹훅 필드 추가 
    * 메시지 발송 결과 코드 업데이트 웹훅에 recipientGroupingKey, senderGroupingKey 필드를 추가하였습니다.
* [Console] 발송 결과 조회 총 건수 표시 개선
    * 발송 결과가 10만 건 이상일 경우 총 건수가 '99,999+건'과 같이 표시되도록 개선하였습니다(기존 1만 건 이상).

### 2023. 07. 25.
* [Console] 파일 업로드를 이용한 템플릿 등록 기능에 신규 필드 추가(v2.3)
    * 파일 업로드를 이용한 템플릿 등록 시 알림톡 아이템리스트, 바로 연결, 대표 링크 등의 신규 필드들이 적용될 수 있도록 개선하였습니다.
* [Console] 본인 인증 절차 개선
    * 본인 인증 반려 및 재요청 시 사용자가 조직에 등록된 사업자등록증을 변경할 수 있게 개선하였습니다.
    * 본인 인증 시 기타 서류 첨부 항목을 추가하였습니다.

### 2023. 06. 27.
* [Console] 발신프로필 조회 시, 신규 필드 추가(v2.3)
    * 카카오톡 채널 스팸 상태(profileSpamLevel), 카카오톡 메시지 스팸 상태(profileMessageSpamLevel) 필드가 추가되었습니다.

### 2023. 05. 30.
* [Console] 알림톡/친구톡 신규 기능 추가(v2.3)
    * 알림톡 아이템리스트형, 톡비즈 플러그인, 비즈니스폼 버튼 타입, 바로연결, 대표링크 기능이 추가되었습니다.
    * 친구톡 비즈니스폼 버튼 타입, 와이드 아이템리스트, 캐러셀 피드형, 쿠폰 기능이 추가되었습니다.
* [Console] 본인 인증 절차 개선
    * KTB 콘솔 사용 시 동일 조직 내에서 한 번만 본인 인증하면 되도록 개선하였습니다.

### 2023. 02. 28.
* [Console] 발송 결과 조회 총 건수 표시 개선
    * 발송 결과가 1만 건 이상일 경우 총 건수가 '9,999+건'과 같이 표시되도록 개선하였습니다.
* [Console] 대량 발송 시 수신자 확인 시점 개선
    * 대량 발송 시 예약 시간을 지정할 경우 예약 시간 전에 수신자를 확인할 수 있도록 개선하였습니다.

### 2023. 01. 31.
* [API] 브랜드톡 기능 종료
    * 카카오 CBT 종료로 인해, 브랜드톡 기능이 종료되었습니다.

### 2022. 11. 29.
* [Console] 발신프로필 최초 사용자 제한
    * 카카오 정책으로 어뷰징 행위 방지를 위해 최초 등록 발신프로필에 대한 제약이 추가되었습니다.
      1. 그룹 프로필에 멤버로 추가 불가
      2. 템플릿 변수가 치환될 때, 그 차이가 14글자를 초과하는 경우, 메시지 발송 실패 처리

### 2022. 10. 25.
* [API] 발신프로필 조회 API isSearchKakaoStatus 필드 삭제
    * 발신프로필 조회 API에서 isSearchKakaoStatus 필드를 삭제하였고, 준실시간 카카오 상태 조회가 가능하도록 개선하였습니다.(6시간 주기로 상태 동기화)
* [API] 알림톡 치환 발송 요청 API buttons 필드 개선
    * 알림톡 치환 발송 요청 API 호출 시, 지정한 ordering의 버튼만 입력해도 정상 발송되도록 개선되었습니다.

### 2022. 08. 23.
* [Console] 알림톡 템플릿 채널추가형(AD)과 복합형(MI) 메시지 유형의 templateAd 일괄 변경
    * 카카오 정책에 따라, "채널 추가하고 이 채널의 광고와 마케팅 메시지를 카카오톡으로 받기" 로 일괄 변경 됩니다.
* [API] 발송 시, 통계 ID 길이 유효성 검사 추가
    * 발송 시 사용되는 statsId 필드 길이 유효성 검사가 추가되었습니다.

### 2022. 07. 26.
* [Console] 브랜드톡 기능 출시
    * 카카오의 CBT 기능인 브랜드톡 기능이 출시되었습니다.
    * CBT 기능이 활성화된 발신 프로필만 사용 가능합니다.
* [API] 알림톡 템플릿 등록/수정 시 templateAd 필드 삭제
    * 알림톡 템플릿 등록/수정 시 templateAd 필드 삭제되었습니다.
    * 채널 추가형(AD) 또는 복합형(MI) 메시지 유형 템플릿 등록 시 templateAd 값이 고정됩니다.

### 2022. 06. 14.
* [Console] 채널 추가형/복합형 템플릿 변경 사항
    * 카카오톡 비즈메시지 정책 변경으로, 채널 추가형/복합형 템플릿인 경우, 채널추가 버튼과 채널 추가 안내 메시지가 고정됩니다.

### 2022. 05. 24.
* [API] 알림톡 템플릿 삭제 개선
    * 반려된 템플릿 이외에 다른 상태의 템플릿도 삭제가 가능하도록 개선되었습니다.
    * 자세한 사항은 [API 가이드](./alimtalk-api-guide/#_50)를 참고하시기 바랍니다.

### 2022. 04. 26.
* [API] SMS 대체 발송 시, 공용 필드 추가
    * 알림톡/친구톡을 SMS로 대체 발송 시, statsId, senderGroupingKey, recipientGroupingKey 필드를 추가하도록 개선하였습니다.
* [API] 알림톡 전문 발송 시, 템플릿 유효성 검증 개선
    * 알림톡 전문 발송 시, 템플릿 치환자에 공백을 허용하도록 유효성 검증을 개선하였습니다.

### 2022. 03. 29.
* [Console] 알림톡 발송 결과 백업 기준일 변경
    * 알림톡 발송 결과 백업 기준일이 180일에서 90일로 변경되었습니다.
* [Console] 일반, 대량, 태그 발송 결과 다운로드 기능 개선
    * Excel 다운로드, 100만 건이 넘는 경우 .zip 파일로 생성하도록 변경되었습니다.

### 2022. 01. 11.
* [Console](구)통계 fade-out
    * 신규 통계 도입으로(구)통계 탭이 삭제되었습니다.
* [Console] 발신프로필 그룹의 멤버 최대 5,000건 제한
    * 카카오 정책에 따라 발신프로필 그룹의 최대 멤버 수를 5,000건으로 제한합니다.
* [Console] CloudTrail 적용
    * CloudTrail이 적용되어, 사용 이력을 확인할 수 있습니다.

### 2021. 12. 02.
* [API] 알림톡 템플릿 문의하기 API 변경
    * 카카오 API 스펙 변경으로 인해, 반려 상태인 템플릿에 대해 문의하면 해당 템플릿이 '검수 중' 상태로 변경됩니다.
* [API] 템플릿 리스트 조회 API 버그 수정
    * categoryCode 필드 값을 정상적으로 응답하도록 수정하였습니다.

### 2021. 10. 26.
* [API] 알림톡/친구톡 대량 발송 조회 API 추가
    * 알림톡/친구톡 대량 발송 조회 API가 추가되었습니다.
* [API] 통계 API 추가
    * 통계 API가 추가되었습니다.
* [API] chatExtra, chatEvent 필드가 추가
    * 메시지 발송 시, BC(상담톡 전환) 타입 버튼에 chatExtra 필드가 추가되었습니다.
    * 메시지 발송 시, BT(봇 전환) 타입 버튼에 chatExtra, chatEvent 필드가 추가되었습니다.
* [API] 웹 링크 타입 버튼에 아웃링크 기능 추가
    * 버튼 클릭 시 인앱 브라우저가 아닌 모바일 기기의 브라우저로 열 수 있는 기능
    * 메시지 발송 시 target 필드가 추가되어, 아웃링크 기능이 추가되었습니다.
* [API] 앱 링크 타입 버튼에 linkMo, linkPc 필드 추가
    * 앱 링크 타입 버튼에 linkMo, linkPc 필드가 추가되었습니다.

### 2021. 08. 24.
* [Console] 이미지 알림톡 기능
    * 이미지 알림톡 기능이 추가되었습니다.

### 2021. 07. 27.
* [Console] 신규 통계 기능
    * 신규 통계가 추가되어 기능이 고도화되었습니다.
    *(구)통계 서비스는 2021년 7월 31일까지 수집되며, 2021년 12월 31일 종료될 예정입니다.

### 2021. 06. 29.
* [Console] 발송 결과 업데이트 시, 웹훅 기능
    * 발송 결과 업데이트 시, 웹훅 기능이 추가되었습니다.

### 2021. 05. 25.
* [Console] 카카오 템플릿 코드 필드 추가
    * 카카오에 실제 등록되는 템플릿 코드 필드가 추가되었습니다.
* [Console] 템플릿 상태/문의 내용 변경 시, 웹훅 기능
    * 템플릿 상태/문의 내용 변경 시, 웹훅 기능이 추가되었습니다.
* [API] 발송 시, price, currencyType 필드 추가
    * 알림톡 광고 모먼트 필드인 price, currencyType 필드가 추가되었습니다.
    * 알림톡 발송 API 및 단건 조회 API messageOption 필드가 추가되었습니다.

### 2021. 04. 27.
* [Console] 동일 발신 프로필 등록 기능 추가
    * 동일 발신 프로필을 다른 프로젝트에 등록 가능하도록 개선되었습니다.
    * 동일 발신 프로필이지만, 프로젝트 간 템플릿/발신 프로필 그룹/발송 이력 등 데이터는 모두 분리됩니다.

### 2021. 03. 23
* [Console] 발신 프로필 그룹 기능 추가
    * 그룹으로 심사 승인된 템플릿은 그룹에 속한 발신 프로필에서 사용할 수 있습니다.
    * 동일한 템플릿을 여러 발신 프로필에서 사용할 때, 유용합니다.
* [Console] 발신 프로필 삭제 기능 추가
    * 상태와 관계 없이, 발신 프로필 삭제 기능이 추가되었습니다.

### 2021. 01. 26
* [Console] 친구톡 발송 결과 백업 기능 추가
    * 친구톡 발송 결과 백업 요청 기능이 추가되었습니다.
    * 콘솔에서 조회한 검색 조건을 기반으로 발송 결과 Excel 파일을 생성할 수 있습니다.
    * 발송 결과 파일은 7일 이후 삭제됩니다.

### 2020. 11. 24.
* [API] 알림톡 템플릿 카테고리 코드 추가
    * 알림톡 템플릿을 등록하거나 수정할 때, 카테고리 코드 필드가 추가되었습니다.
    * 카테고리를 입력한 템플릿을 우선 심사합니다.
* [Console] 알림톡 180일이 지난 알림톡 발송 목록 데이터 백업 기능 추가
    * 180일이 지난 발송 목록(일반/대량)에 대해 고객의 오브젝트 스토리지 또는 AWS S3로 백업 파일을 생성해주는 기능이 추가되었습니다.
    * 백업 설정은 발송 설정 탭에서 확인 가능합니다.
* [API] 알림톡 템플릿 코드 제한 변경
    * 알림톡 templateCode 필드에(영문, 숫자, -, _)를 사용할 수 있도록 변경되었습니다.

### 2020. 10. 27.
* [API] 알림톡 PC 노출/미노출 필드 변경
    * pcFlag에서 securityFlag로 필드가 변경되었습니다.(default: false)
    * 보안 템플릿 여부를 나타내는 필드로, OTP등 보안 메시지일 경우 설정해야 합니다.
    * true로 등록되면, 메인 디바이스를 제외한 모든 디바이스에 메시지 텍스트가 나타나지 않습니다.
* [API] 알림톡 채널 추가 버튼 타입 변경
    * 채널 추가 버튼 타입이 CA에서 AC로 변경되었습니다.
    * 채널 추가 버튼은 버튼 목록 중, 최상단 혹은 단독으로 있을 때만 등록 가능합니다.
    * 채널 추가 버튼명은 '채널 추가'만 가능합니다.
    * AC로 변경한 버튼은 하이라이트 처리와 아이콘이 보이는 새로운 버튼 형태로 노출됩니다.
* [Console] 알림톡 발송 결과 백업 기능 추가
    * 알림톡 발송 결과 백업 요청 기능이 추가되었습니다.
    * 콘솔에서 조회한 검색 조건을 기반으로 발송 결과 Excel 파일을 생성할 수 있습니다.
    * 발송 결과 파일은 7일 이후 삭제됩니다.
* [Console] 친구톡 발송 결과 상세 조회 모달 개선
    * 친구톡 발송 결과 상세 조회할 때, 광고 여부와 대체 발송 요청 결과를 추가적으로 확인할 수 있습니다.

### 2020. 08. 25.
* [API] 알림톡 PC 노출/미노출 기능
    * 템플릿 등록 시, PC 노출/미노출을 선택할 수 있는 기능이 추가되었습니다.
* [Console] 대량 발송 Excel 파일 지원
    * 대량 발송 시, Excel 형식의 수신자 목록 파일도 업로드할 수 있게 수정했습니다.

### 2020. 07. 28.
* [API] 알림톡 강조 표기 템플릿 기능
    * CBT가 종료되어, 정식 기능으로 추가되었습니다.
* [API] 알림톡 템플릿 메시지 유형 확대
    * 알림톡 템플릿 메시지 유형이 확대 되었습니다(BA: 기본형, EX: 부가 정보형, AD: 채널 추가형, MI: 복합형).
* [API] 알림톡 템플릿 첨부 파일 문의 기능
    * 알림톡 템플릿 문의 시, 파일을 첨부하여, 문의하는 기능이 추가되었습니다.

### 2020. 06. 23.
* [API] 알림톡 강조 표기 템플릿 기능
    * 템플릿 등록 API에 강조 템플릿을 사용할 수 있도록 변경되었습니다.(CBT 기능)

### 2020. 05. 26.
* [API] 친구톡 와이드 이미지 기능
    * 친구톡 와이드 이미지를 업로드해 발송할 수 있는 기능이 추가되었습니다.
* [Console] 토큰 미등록 플러스친구 삭제 기능
    * 토큰 미등록 플러스친구 삭제 기능이 추가되었습니다.

### 2019. 11. 26.
* [Console] 파일 업로드를 이용한 템플릿 등록 기능
    * 대량의 템플릿을 등록할 수 있는 파일 업로드 기능이 추가되었습니다.
* [Console] 템플릿 조회 기능 개선
    * 원본 템플릿 상태와 최종 템플릿 승인 상태를 모두 조회할 수 있는 기능이 추가되었습니다.
* [Console] 발송 결과 조회 시, 등록 일시 조회 기능
    * 발송 결과 조회 시, 등록 일시 기준으로 조회하는 기능이 추가되었습니다.


### 2019. 10. 29.
* [API] 인증 메시지 발송 시 인증 문구 유효성 검사 강화
    * 인증용 메시지 발송 시 인증 문구가 포함되어 있지 않은 경우 메시지 발송이 불가능합니다.
    * 자세한 사항은 [[API 가이드](./alimtalk-api-guide/#precautions-authword)] 참고하시기 바랍니다

### 2019. 09. 24.
* [Console] 알림톡/친구톡 예약발송 취소 기능 추가
    - 알림톡/친구톡 예약 발송 시, 발송 결과 조회 탭에서 발송 전이라면 예약을 취소할 수 있는 기능이 추가되었습니다.
    - 예약 발송 요청 후, 해당 시간을 조회하면 체크박스가 노출되고 선택하고 취소 버튼을 눌러 취소할 수 있습니다.
* [Console] 알림톡/친구톡 대량 발송 파일 업로드 시 유효성 검증 추가
    - 대량 발송 파일 업로드 시에 유효성 검증을 하여 발송하기 전에 피드백을 받을 수 있게 되었습니다.
* [Console] 알림톡/친구톡 대량 발송 최대 수신자 증가
    - 알림톡/친구톡 대량 발송 최대 수신자가 10,000명에서 100,000명으로 증가하였습니다.
* [Console] 카카오톡 플러스 친구에서 카카오톡 채널로 문구 변경
    - 2019년 9월 17일자로 '플러스 친구'에서 '카카오톡 채널'로 서비스 명이 변경되었습니다.

### 2019. 07. 30.
* [Console] 대체 발송된 SMS 요청 결과 코드 필드 추가
    - 대체 발송된 메시지 상세 조회 시, SMS 요청 결과 코드가 추가되었습니다.
* [System] 서비스 안정화를 위한 서버 교체 작업

### 2019. 06. 27.
* [Console] 친구톡 대량 발송 시, <b>대체 발송 지정 기능, 분할 발송 기능</b> 추가
    - 대체 발송 내용, 발신 번호, 대체 발송 여부 등 대체 발송 관련 필드를 지정할 수 있는 기능을 추가했습니다.
    - 분할 횟수, 시간 간격을 지정 분할 발송할 수 있는 기능이 추가되었습니다.
* [API] 친구톡 예약 발송 취소 API 추가
    - 친구톡 예약 메시지를 발송 전이라면 취소할 수 있습니다.
* [API] 인증 알림톡 예약 발송 취소 API 추가
    - 인증 알림톡 예약 메시지를 발송 전이라면 취소할 수 있습니다.
* [Console] 알림톡/친구톡 대량 발송 개선
    - [검수 후 진행] 기능을 이용할 경우, [발송] 버튼을 누르지 않으면 알림 메일이 발송됩니다.
      + 메일 수신 대상자: 프로젝트 멤버 전체
      + 메일 발송 조건: [검수 후 진행] 클릭한 뒤 1일 후 1번, 6일 후 1번 총 2회 발송
    - 대량 예약 발송 시, 검수 후 진행 기능을 이용할 수 없습니다.
* [Console] 플러스친구 조회 화면 개선
    - 플러스친구 조회 시, 조건 검색 기능을 추가했습니다.
* [Console] 문구 버그 수정
    - 플러스친구 상태, 템플릿 삭제 문구 오류가 있어 수정하였습니다.
* [Console] 플러스친구 등록 시, <b>비즈니스 인증 도입</b>
    - 플러스친구 등록 시 플러스친구의 <b>비즈니스 인증</b>된 경우만 등록 가능하도록 변경됩니다.​ [[관련 공지사항](https://center-pf.kakao.com/notices/311)]

### 2019. 05. 28.
* [API] 발송 시, 국가 코드가 포함된 수신 번호 발송 기능
    - 발송 시, recipientNo 필드에 국가 코드를 입력할 수 있도록 개선되었습니다.
    - 카카오 앱에서 해외 휴대폰 번호로 인증한 사용자에게 발송 가능합니다.
* [API] 알림톡 발송 v1.3 추가
    - 알림톡 발송 API의 대체 발송 관련 필드 형상이 친구톡 발송 API와 동일하게 개선되었습니다.
* [API] 대체 발송 설정 API 추가
    - 플러스친구 대체 발송 설정 API가 추가되었습니다.
* [API] 플러스친구 조회 API 개선
    - 플러스친구 조회 API에 pagination 기능이 추가되었습니다.
    - 플러스친구 조회 API에 알림톡/친구톡 대체 발송 응답 필드가 추가되었습니다.(v1.3)

### 2019. 04. 30.
* [Console] 플러스친구 등록 시, 비지니스 인증 방식 롤백
    - 플러스친구의 비지니스 인증이 장시간 소요되어, 플러스친구 등록 방식을 이전 방식으로 변경하였습니다.

### 2019. 04. 23.
* [Console] 알림톡 대량 발송 시, <b>대체 발송 지정 기능, 분할 발송 기능</b> 추가
    - 대체 발송 내용/발신번호/대체 발송 여부 등 대체 발송 관련 필드를 지정할 수 있는 기능이 추가되었습니다.
    - 분할 횟수/시간 간격을 지정하여 분할 발송할 수 있는 기능이 추가되었습니다.
* [Console] 알림톡/친구톡 <b>대체 발송 설정 분리</b>
    - 알림톡/친구톡 각각의 플러스친구에 대체 발송 설정을 할 수 있는 기능이 추가되었습니다.
    <br>ex) 동일한 플러스친구에서 알림톡만 대체 발송 설정 시, 친구톡은 발송 실패하여도 대체 발송 되지 않습니다.
* [Console] 플러스친구 등록 시, <b>비지니스 인증 도입</b>
    - 플러스친구 등록 시 플러스친구의 <b>비즈니스 인증</b>된 경우만 등록 가능하도록 변경됩니다.​ [[관련 공지사항](https://center-pf.kakao.com/notices/311)]
* [Console] 템플릿 선택 모달창에서 like 검색 기능 추가
    - 템플릿 선택 모달창에서 손쉽게 템플릿을 선택할 수 있도록 like 검색 기능이 추가되었습니다.(템플릿코드, 템플릿명으로 검색)
* [API] 광고 친구톡, <b>광고 SMS API로 대체 발송</b> 되도록 개선
    - 광고 친구톡 발송 실패 시, 광고 SMS API로 대체 발송 되도록 개선되었습니다.
    - 광고 친구톡 대체 발송 설정 시, 080수신거부번호를 반드시 등록해야 정상적으로 대체 발송 됩니다.
* [API] 친구톡 발송 API 대체 발송 고도화
    - 발송 시, 대체 발송 제목 필드가 추가 되었습니다.
    - 대체 발송 필드를 이용하여, 대체 발송 될 제목/내용/발신번호/080수신거부번호/대체 발송 유무를 선택할 수 있습니다.
* [API] 알림톡/친구톡 발송 요청 실패 메시지 저장하지 않도록 개선
    - 발송 수신자 길이 제한, 유효하지 않은 수신번호 등 요청 오류로 인한 메시지는 저장하지 않도록 개선되었습니다.
    - API 응답 필드 sendResults 필드를 통해 요청 성공/실패를 확인할 수 있습니다.

### 2019. 03. 26.
* [Console] 알림톡 미리보기 UI 추가
    - 알림톡 수신 화면 미리보기 UI가 추가 되었습니다.
* [API] 인증용 알림톡 발송을 위한 Auth API 추가
    - 인증용 알림톡 발송을 위해 Auth용 API가 추가되어, 발송 pool이 분리되었습니다.

### 2019. 02. 26.
* [Console] 알림톡 대량 발송 시, 발송 실패 버그 수정
    - 일부 유효하지 않은 수신번호로 인해, 발송 실패되는 버그를 수정하였습니다.
* [Console] 친구톡 대량 발송 수신번호 마스킹되는 버그 수정
    - 친구톡 대량 발송 수신자 상세 조회 시, 수신번호 마스킹되는 버그를 수정하였습니다.

### 2019. 01. 29.
* [API] 친구톡 v1.2 API 추가
    - 발송 시, 발신/수신자 그룹핑키 필드가 추가되었습니다.
    - 발송 응답 필드에 각 수신자 별 <b>요청 성공/실패</b> 필드가 추가되었습니다.
* [API] 친구톡 발송 결과 업데이트 조회 API 추가
    - 결과 업데이트 시간으로 조회할 수 있는 신규 API가 추가되었습니다.
* [Console] 알림톡 발송 화면 고도화
    - 복수의 수신자에게 발송할 수 있게 개선되었습니다.
    - 예약 발송을 할 수 있게 개선되었습니다.
    - 대체 발송 내용을 선택할 수 있게 개선되었습니다.
* [Console] 친구톡 대량 발송 기능 추가
    - csv 파일을 이용하여, 대량 발송 기능이 추가되었습니다.
* [Console] 친구톡 대량 발송 조회 기능 추가
    - 친구톡 대량 발송 조회 탭에서 대량 발송한 메시지를 조회할 수 있습니다.
* [Console] 알림톡 템플릿 수정 기능 고도화
    - 기존 반려 상태의 템플릿만 수정할 수 있었지만, 승인 상태의 템플릿도 수정할 수 있도록 개선되었습니다.
    - 승인 상태의 템플릿을 수정 시 재검수를 받게 되고 재검수 후, 승인된 템플릿은 <b>기존 템플릿의 내용과 대체</b>됩니다.
    - 재검수를 받는 동안, 이전 승인된 템플릿은 정상적으로 발송 가능합니다.
* [Console] 수신 번호 마스킹 기능 추가
    - 별도 요청한 프로젝트는 수신 번호 마스킹 기능이 추가되었습니다.
* [Console] 알림톡 템플릿 본문 글자 수 검사 버그 수정
    - 템플릿 본문 중, 공백이 2글자로 계산되는 버그 수정되었습니다.

### 2018. 12. 04.
* [API] 알림톡 v1.2 API 추가
    - 발송 시, 발신/수신자 그룹핑키 필드가 추가되었습니다.
    - 발송 응답 필드에 각 수신자 별 <b>요청 성공/실패</b> 필드가 추가되었습니다.
* [API] 알림톡 발송 결과 업데이트 조회 API 추가
    - 결과 업데이트 시간으로 조회할 수 있는 신규 API가 추가되었습니다.
* [API] 발송 시, 대체 발송 발신번호 필드 추가
    - 발송 시, resendSendNo 필드를 통하여 대체 발송 발신번호를 지정할 수 있는 기능이 추가되었습니다.
* [API] 발송 메시지 90일까지 보관하도록 개선
    - 조회 시, 90일 이전 데이터는 조회되지 않도록 개선되었습니다.
* [Console] 플러스친구 상세 상태 추가
    - 플러스친구 조회 화면에 TOAST 플러스친구, 카카오 플러스친구, 카카오 플러스친구 프로필 상태 필드가 추가되었습니다.

### 2018. 11. 13.
* [API] 알림톡 발송 API 대체 발송 고도화
    - 발송 시, 대체 발송 제목 필드가 추가 되었습니다.
    - 대체 발송 제목 필드를 이용하여, LMS로 대체 발송 시, 제목을 지정할 수 있습니다.
    - 템플릿 본문 불일치(-3010), 템플릿 버튼 불일치(-3011)으로 요청 실패할 경우, 대체 발송 되도록 변경되었습니다. 대체 발송이 필요없는 메시지는 isResend 필드를 이용하여, 조작 가능합니다.
* [API] 예약 발송 버그 수정
    - 예약 발송 시, 요청 아이디의 일자 데이터 오류로 인해, 예약 발송 취소가 정상적으로 되지 않는 버그를 수정하였습니다.

### 2018. 10. 23.
* [API] 알림톡 발송 API 예약 기능 추가
    - 예약 기능을 사용하여 원하는 시간에 메시지를 발송할 수 있습니다.
    - 예약한 메시지가 발송 전이라면 언제든지 취소할 수 있습니다.
    - 자세한 사항은 [[알림톡 발송 API](./alimtalk-api-guide/#_3)] 를 참고하시기 바랍니다.
* [API] 알림톡 발송 API 대체 발송 고도화
    - 발송 시, 대체 발송 타입(SMS/LMS), 대체 발송 여부(true/false), 대체 발송 내용 필드가 추가 되었습니다.
    - 해당 필드를 사용하여, 대체 발송을 더 확장성 있게 사용할 수 있습니다.
* [API] 플러스친구, 템플릿 관련 API 추가
    - 플러스친구 카테고리 조회, 사업자등록증 업로드, 등록, 토큰 인증, 리스트 조회 API가 추가되었습니다.
    - 템플릿 등록, 수정, 삭제, 문의하기 API가 추가되었습니다.
* [Console] 템플릿 코드 Like 검색 기능 추가
    - Console에서 템플릿 조회 시, Like 검색 기능이 추가되었습니다.

### 2018. 08. 28.
* [Console] 발송 결과 조회 개선
    - 알림톡 발송 결과 조회 시, 템플릿 코드를 직접 입력할 수 있도록 개선되었습니다.

### 2018. 07. 24.
* [Console] 서비스명 변경
    - AlimTalk 에서 KakaoTalkBizmessage로 서비스명이 변경되었습니다.
* [Console] 친구톡 기능 추가
    - 친구톡은 친구를 맺은 이용자를 대상으로 하며, 광고성 메시지도 발송이 가능합니다.
    - 콘솔에서 메시지 발송, 조회, 이미지 관리, 통계 기능을 제공합니다.
    - 자세한 사항은 [[친구톡 개요](./friendtalk-overview/)] 를 참고하시기 바랍니다.
* [API] 친구톡 API 추가
    - 친구톡 API는 메시지 발송, 목록 조회, 단건 조회, 이미지 관리 기능을 지원합니다.
    - 자세한 사항은 [[친구톡 API 가이드](./friendtalk-api-guide/)] 를 참고하시기 바랍니다.
* [API] 알림톡, 친구톡 일별 발송 제한 추가
    - 7월 24일 점검 이후, 생성된 플러스 친구에 한하여, 일별 1,000건의 발송량 제한 기능이 추가 되었습니다.
    - 일별 최대 발송량이 초과한 발송 요청건은 실패 처리됩니다.
* [API] 발송 실패 재발송 기능 수정
    - 재발송 본문 내용이 아래와 같이 수정되었습니다.

```
발송 본문 내용
- 웹 링크 버튼명: 웹 링크
- 웹 링크 버튼명2: 웹 링크2
...
```

### 2018. 06. 26.
#### 기능 개선
* [Console] 플러스친구 등록 시, 요청 필드 추가
    - 카카오 발급절차 강화로 인해 사업자등록번호, 사업자 카테고리를 입력받도록 수정되었습니다.

#### 버그 수정
* [Console] 통계 차트 버그 개선 버전으로 변경
    - IE 브라우져에서 Export xls 기능 버그 개선 버전으로 변경하였습니다.

### 2018. 05. 29.
#### 기능 추가
* [API] 발송 결과 단건 조회 API 추가
    - 특정 발송 결과를 조회할 수 있는 API가 추가되었습니다.
    - 자세한 사항은 [[알림톡 API 가이드](./alimtalk-api-guide/#_14)] 를 참고하시기 바랍니다.
* [API] 발송 결과 리스트 조회 API v1.1 추가
    - 응답에 recipientSeq(수신자 시퀀스) 필드가 추가되면서, v1.1 API가 추가되었습니다.

#### 버그 수정
* [API] 치환 발송 API 버그 수정
    - Request Body의 templateParameter 필드가 필수 값으로 인식되는 버그가 개선되었습니다.

### 2018. 04. 24.
#### 기능 추가
* [Console] 템플릿 챗버블 기능 추가
    - 다중 버튼 템플릿 기능이 추가되었습니다.
    - 버튼 타입 추가되었습니다.( 배송 조회, 웹 링크, 앱 링크, 봇 키워드, 메세지 전달 )
* [API] 템플릿 조회 API 추가
    - 템플릿을 조회할 수 있는 API가 추가되었습니다.
    - 자세한 사항은 [[알림톡 API 가이드](./alimtalk-api-guide/#_46)] 를 참고하시기 바랍니다.

#### 기능 개선/변경
* [API] 발송 실패 재발송 기능 수정
    - 본문 길이에 따라 SMS/LMS로 구분지어 발송하도록 수정되었습니다.
    - 재발송 본문 내용이 수정되었습니다.( 본문 + 웹 링크 버튼명 + 버튼 링크 )

### 2018. 03. 22.
#### 기능 추가
* [Console] 템플릿 수정, 삭제, 문의 등록 기능 추가
    - 템플릿 수정, 삭제 기능이 추가되었습니다.
    - 검수 담당자에게 문의를 등록 기능이 추가되었습니다.
    - 자세한 사항은 [[알림톡 콘솔 사용 가이드](./alimtalk-console-guide/#_12)] 를 참고하시기 바랍니다.
* [API] 전문 발송 API 추가
    - 치환 데이터가 아닌 전문 내용으로 발송할 수 있는 API가 추가되었습니다.
    - 자세한 사항은 [[알림톡 API 가이드](./alimtalk-api-guide/#_4)] 를 참고하시기 바랍니다.

### 2018. 02. 22.
#### 기능 추가
* [Console] 대량 발송 기능 추가
    - csv 파일을 이용하여, 대량 발송 기능이 추가되었습니다.

### 2018. 01. 25.
#### 기능 개선/변경
* [Console] 템플릿 등록 개선
    - 버튼명 앞뒤 공백 제거 기능이 추가 되었습니다.
    - 길이 제한 수정되었습니다.( 템플릿 코드: 10자 -> 20자, 버튼명: 10자 -> 14자)
    - 배송 조회 템플릿 등록 시, 버튼명을 직접 입력할 수 있게 수정되었습니다.

#### 기능 추가
* [API] 발송 결과 조회 API 추가

### 2017.11.23.
#### 기능 추가
* [Console] 다중 플러스친구 등록
    - 1개의 플러스친구 등록 구조에서 다중 플러스친구 구조로 변경되었습니다.
* [Console] 템플릿 반려 시, 템플릿 상세보기에서 반려 사유 제공.
* [API] 다중 플러스친구 적용에 따른 발송 API 필드 추가
    - requestBody에 plusFriendId 필드12가 추가되었습니다.
    - plusFriendId 필드를 입력하지 않을 경우, 처음 등록된 플러스친구 ID로 발송됩니다.

### 2017.08.24.
#### 기능 추가
* [Console] 알림톡 발송 통계 화면 제공
    - 날짜별/시간대별/요일별 통계 화면이 제공됩니다.
    - 발송한 일자와 템플릿으로 조회할 수 있습니다.

#### 기능 개선/변경
* [Console] 자유버튼 템플릿 등록 시 URL 검증 변경
    - 자유버튼에 URL 등록 시, http:// or https:// 가 필수로 포함 -> #{url}과 같이 템플릿 치환자도 등록할 수 있게 변경하였습니다.
    - 템플릿 치환자 #{url} 형식의 템플릿 치환자가 아닐 경우 http:// or https:// 검증은 유지됩니다.
* [API] Content-type 에러 응답 메세지 수정
    - 요청 header에 Content-type: application/json이 아닐 경우 실패 응답 메세지 수정되었습니다.

### 2017. 07. 20.
#### 기능 추가
* [Console] 알림톡 발송 결과 조회 추가
    - 발신 일시, 수신번호, 템플릿 등의 조건으로 발신한 메세지의 전송 결과를 조회할 수 있습니다.

### 2017. 06. 22.
#### 기능 개선/변경
* [Console] 발신프로필 관리 페이지 추가
* [Console] 테스트 발송 페이지 추가
* [Console] 템플릿 등록 조회 페이지 추가

#### 기능 추가
* [Console] 발송 실패 설정 추가
    - 알림톡 발송 실패 시, LMS로 대체 발송하는 기능
* [Console] 템플릿 자유 버튼 타입에 링크 치환 기능
    - 템플릿 자유 버튼 타입일 경우, 버튼 링크를 치환자로 등록 가능. ex) buttonURL: #{url}


### 2017. 05. 25.
#### 기능 개선/변경
* [Console] 메인페이지 마크업 개선

### 2017. 04. 20.
#### 신규 상품 출시
* AlimTalk은 휴대폰 번호를 기반으로 친구 추가 없이 카카오톡 사용자에게 배송, 예약 시간 등의 정보성 메시지를 발송할 수 있는 상품입니다.
* 손쉬운 연동을 위한 RESTful API를 제공합니다.