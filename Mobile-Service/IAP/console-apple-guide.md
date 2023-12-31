# Apple 콘솔 가이드

### Mobile Service > IAP > Apple 콘솔 가이드

Apple 구독 상품 결제를 사용하려면 App Store Connect에서 secret key 생성 및 Notification url 설정이 필요합니다.\
Secret Key는 IAP 앱 정보에 등록합니다.\
Apple 일반 상품 결제는 특별한 설정이 필요하지 않습니다.

> 참고 https://help.apple.com/app-store-connect/#/devf341c0f01

### shared secret key 생성하기

```
shared secret key은 모든 앱에 공통인 마스터키로 생성할 수 있고 앱 별로 생성할 수도 있습니다.
secret key를 IAP 앱 정보에 등록합니다.
```

#### master shared secret key

```
1. App Store Connect
2. [My Apps] 클릭
3. [Master Shared Secret] 클릭
```

![\[\]](http://static.toastoven.net/prod\_iap/iap-console-apple-shared-key-1.png)

\


#### 앱 별 shared secret key

```
1. App Store Connect
2. [My Apps] 클릭 > 생성 하려는 [앱] 클릭 > toolbar에서 [Features] 클릭
3. [App-Specific Shared Secret] 클릭
```

![\[\]](http://static.toastoven.net/prod\_iap/iap-console-apple-shared-key-2.png)

#### IAP 앱 정보에 shared secret key 입력하기

```
1. IAP Console > App > ios 앱 선택
2. Apple Shared Secret 입력
```

![\[\]](http://static.toastoven.net/prod\_iap/iap-console-apple-edit.png)

### Notification url 등록하기

**Notification V2**는 아직 지원하지 않습니다. **V1**을 사용하십시오.

```
1. App Store Connect > 나의 앱 > 앱 정보 > 일반 정보 
2. 구독 상태 URL 에 IAP url을 등록합니다.
- URL : https://api-iap.cloud.toast.com/callback/subscription/{YOUR_PACKAGE_NAME}/AS
- {YOUR_PACKAGE_NAME} : app bundle id
```
