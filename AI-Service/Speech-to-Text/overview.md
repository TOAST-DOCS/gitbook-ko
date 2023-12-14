## AI Service > Speech to Text > 개요

Speech to Text(STT)는 NHN Cloud의 음성 인식 및 문자 합성 기술을 통해, 입력된 음성을 인식하고, 인식된 음성을 텍스트로 변환하여 제공합니다. 음성 받아쓰기, 음성을 통한 디바이스 제어, 음성 챗봇 서비스 등 음성을 문자로 변환해서 이용하는 다양한 분야에 적용할 수 있습니다.

## 주요 기능

* **음성 인식**
    * 입력된 음성에서 NHN Cloud의 Speech to Text 엔진을 통해 음성을 인식하고 변환된 텍스트를 제공합니다.
    * 음성 인식은 한국어에 한해 합성 결과를 제공합니다.

* **다양한 방식의 음성 입력 지원**
    * 인식할 음성을 음성 파일로 업로드할 수 있습니다.
    * 마이크로 음성을 녹음하여 음성 입력을 할 수 있습니다.

* **인식 결과 다운로드 지원**
    * JSON, TXT 파일을 다운로드할 수 있습니다.
    * 음성 인식 결과 파일을 다운로드하여 원하는 결과로 수정할 수 있습니다.

## 음성 입력 가이드

보다 정확한 음성 인식을 위해 아래의 가이드를 참고하시기 바랍니다.

* 음성 파일 업로드 지원 형식: WAV, WebM, MP3, OGG, FLAC, AAC, AC3
* 최대 용량: 3MB
* 음성 파일 인식 가능 시간: 최소 0.36초, 최대 60초
* 권장 사항
    * 파일 형식: WAV
    * 비트: 16bit
    * 샘플 레이트: 16kHz
    * 채널 수: 모노(mono)
    * 음성 파일 시간: 10초
* 최대한 조용한 환경에서 녹음해 주시기 바랍니다.

## 서비스 대상
* 음성을 자동으로 받아쓰는 기능 구축이 필요한 경우(고객 센터 상담, 자막 생성 등)
* 음성을 통한 디바이스 제어가 필요한 경우(IoT 디바이스 등)
* 음성 챗봇 서비스를 구축하는 경우

## 개인정보 처리에 대한 안내
* Speech to Text 서비스를 이용하는 과정에서 고객은 이용자의 개인정보를 수집/이용할 수 있으며, 이 경우 고객은 개인정보보호법 등 관련 법령을 준수할 의무가 있습니다. 또한, 본 서비스를 이용함에 따라 고객은 NHN Cloud에 개인정보 처리에 관한 업무를 위탁 및 제공하게 됩니다. 위탁자의 지위에 있는 고객은 수탁사인 NHN Cloud와 별도 서면에 의한 개인정보 처리 업무 위탁 계약을 체결할 수 있으며, 고객이 운영하는 개인정보처리방침에 아래 내용을 참고하여 고지할 수 있고 이용자로 부터 개인정보의 제3자 제공에 관한 동의를 얻어야 합니다.
    - 수탁 업체: 엔에이치엔클라우드㈜
    - 위탁 업무의 내용: Speech to Text 서비스 제공