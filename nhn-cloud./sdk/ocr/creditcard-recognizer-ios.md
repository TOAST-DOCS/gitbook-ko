# Credit Card (iOS)

### NHN Cloud > SDK 사용 가이드 > OCR > Credit Card (iOS)

### 사전 준비

1. [NHN Cloud SDK](../../../nhncloud/nhncloud-sdk/getting-started-ios/)를 설치합니다.
2. [NHN Cloud Console](https://console.nhncloud.com)에서 \[AI Service > OCR] 서비스를 활성화합니다.
3. OCR 콘솔에서 AppKey와 SecretKey를 확인합니다.

\


### 지원 환경

NHN Cloud OCR은 iOS 11.0 이상에서 동작합니다.\


### NHN Cloud OCR 구성

iOS용 NHN Cloud OCR SDK의 구성은 다음과 같습니다.

| Service   | Cocoapods Pod Name                    | Framework                                                 | Dependency                                            | Build Settings                                        |
| --------- | ------------------------------------- | --------------------------------------------------------- | ----------------------------------------------------- | ----------------------------------------------------- |
| OCR       | NHNCloudOCR                           | NHNCloudOCR.framework                                     | <p>* Vision.framework<br>* AVFoundation.framework</p> |                                                       |
| Mandatory | <p>NHNCloudCore<br>NHNCloudCommon</p> | <p>NHNCloudCore.framework<br>NHNCloudCommon.framework</p> |                                                       | <p>OTHER_LDFLAGS = (<br>"-ObjC",<br>"-lc++"<br>);</p> |

### NHN Cloud OCR SDK를 Xcode 프로젝트에 적용

#### 1. Cococapods을 통한 적용

* Podfile을 생성하여 NHN Cloud SDK에 대한 Pod을 추가합니다.

```podspec
platform :ios, '11.0'
use_frameworks!

target '{YOUR PROJECT TARGET NAME}' do
    pod 'NHNCloudOCR'
end
```

#### 2. Swift Package Manager를 사용해 NHN Cloud SDK 적용

* XCode에서 **File > Add Packages...** 메뉴를 선택합니다.
* Package URL에 'https://github.com/nhn/nhncloud.ios.sdk'를 넣고 **Add Package** 버튼을 선택합니다.
* NHNCloudOCR을 선택합니다.

![swift\_package\_manager](https://static.toastoven.net/toastcloud/sdk/ios/swiftpackagemanager01.png)

**프로젝트 설정**

* **Build Settings**의 **Other Linker Flags**에 \*\*-lc++\*\*와 **-ObjC** 항목을 추가합니다.
  * **Project Target > Build Settings > Linking > Other Linker Flags** ![other\_linker\_flags](https://static.toastoven.net/toastcloud/sdk/ios/overview\_settings\_flags\_202206.png)

#### 3. 바이너리를 다운로드하여 NHN Cloud SDK 적용

**프레임워크 설정**

* NHN Cloud [Downloads](../../../Download/#toast-sdk) 페이지에서 전체 iOS SDK를 다운로드할 수 있습니다.
* Xcode Project에 **NHNCloudOCR.framework**, **NHNCloudCore.framework**, **NHNCloudCommon.framework, vision.framework, AVFoundation.framework**를 추가합니다.
* vision.framework와 AVFoundation.framework는 아래 방법으로 추가할 수 있습니다. ![linked\_vision\_frameworks](https://static.toastoven.net/toastcloud/sdk/ios/linked\_vision\_frameworks.png) ![linked\_avfoundation\_frameworks](https://static.toastoven.net/toastcloud/sdk/ios/linked\_avfoundation\_frameworks.png) ![linked\_frameworks\_ocr](https://static.toastoven.net/toastcloud/sdk/ios/linked\_frameworks\_ocr.png)

**프로젝트 설정**

* **Build Settings**의 **Other Linker Flags**에 \*\*-lc++\*\*와 **-ObjC** 항목을 추가합니다.
  * **Project Target > Build Settings > Linking > Other Linker Flags** ![other\_linker\_flags](https://static.toastoven.net/toastcloud/sdk/ios/overview\_settings\_flags\_202206.png)

### NHNCloudOCR SDK 초기화

* NHN Cloud Console에서 발급 받은 AppKey와 Secret을 NHNCloudOCRConfiguration 객체에 설정합니다.
  * AI Service -> OCR -> Document OCR -> 신용카드
* NHNCloudOCR은 초기화에 NHNCloudOCRConfiguration 객체를 파라미터로 사용합니다.
* 카메라 사용 권한을 얻기 위해 info.plist에 아래 내용을 추가합니다.

```
Key : NSCameraUsageDescription
Value : [카메라 권한 요청 메시지]
```

#### 초기화 API 명세

```objc
// 초기화
+ (void)initWithConfiguration:(NHNCloudOCRConfiguration *)configuration;

// Delegate 설정
+ (void)setCreditCardRecognizerDelegate:(nullable id<NHNCloudCreditCardRecognizerDelegate>)delegate;
```

#### Delegate API 명세

* NHNCloudCreditCardRecognizerDelegate를 등록하면 인식 결과에 대한 통지를 받을 수 있습니다.
* OCR이 실행 중일 때 화면의 스크린 캡처와 동영상 녹화 이벤트를 수신할 수 있습니다.
* SDK에서 제공하는 기본 화면 사용 시(NHNCloudCreditCardRecognizerViewController 상속 구현) 닫기, 확인 이벤트를 수신할 수 있습니다.

```objc
@protocol NHNCloudCreditCardRecognizerDelegate <NSObject>

// 신용카드 인식 결과 반환
- (void)didDetectCreditCardInfo:(nullable NHNCloudCreditCardInfo *)cardInfo error:(nullable NSError *)error;

@optional

// 스크린 캡처 이벤트 수신
- (void)didDetectCreditCardSecurityEvent:(NHNCloudSecurityEvent)event;

// 닫기 버튼 이벤트 수신(NHNCloudCreditCardRecognizerViewController 상속 구현 시에만 수신 가능)
- (void)creditCardRecognizerViewControllerCancel;

// 확인 버튼 이벤트 수신(NHNCloudCreditCardRecognizerViewController 상속 구현 시에만 수신 가능)
- (void)creditCardRecognizerViewControllerConfirm;

@end
```

#### 검출 이미지 반환 설정하기

* OCR 결과인 NHNCloudCreditCardInfo 데이터에 검출된 이미지를 함께 반환 받을 수 있습니다.
  * 기본값은 비활성화입니다.

**검출 이미지 반환 설정 API 명세**

```objc
@interface NHNCloudOCR : NSObject
//..
+ (void)setDetectedImageReturn:(BOOL)enable;
+ (BOOL)isEnableDetectedImageReturn;
//..
@end
```

#### 인식 영역 표시하기

**인식 영역 반환 API**

* OCR 결과인 NHNCloudCreditCardInfo 데이터에 인식된 영역의 좌표 정보를 반환 받을 수 있습니다.

```objc
@interface NHNCloudCreditCardInfo : NSObject

// 카드 번호 인식 영역
@property(nonatomic, strong, readonly, nullable) NSArray<NSValue *> *numberBoundingBoxes;

// 유효 기간 인식 영역
@property(nonatomic, assign, readonly) CGRect validThruBoundingBox;

@end

```

**인식 영역 ImageView에 그리기**

```objc

- (void)viewDidLoad {
    [super viewDidLoad];
    // 인식된 이미지를 반환하도록 설정
    [NHNCloudOCR setDetectedImageReturn:YES];
}

// 신용카드 인식 결과 반환
- (void)didDetectCreditCardInfo:(nullable NHNCloudCreditCardInfo *)cardInfo error:(nullable NSError *)error {

    if (cardInfo.detectedImage != nil) {
        UIImageView *imageView = [[UIImageView alloc] initWithImage:cardInfo.detectedImage.image];
        imageView.contentMode = UIViewContentModeScaleAspectFit;
          
        UIGraphicsBeginImageContextWithOptions(imageView.frame.size, NO, 0.0);
        CGContextRef context = UIGraphicsGetCurrentContext();

        [imageView.image drawInRect:CGRectMake(0, 0, imageView.frame.size.width, imageView.frame.size.height)];
        
        // 카드 번호의 인식 영역을 그린다.
        for (NSValue *rectValue in cardInfo.numberBoundingBoxes) {
            CGRect scaledBoundingBox = [self dividedRect:rectValue.CGRectValue
                                                 // 디바이스의 해상도를 고려해 scale의 값만큼 좌표를 나눈다.
                                                   scale:[UIScreen mainScreen].scale];
            CGContextSetStrokeColorWithColor(context, [UIColor orangeColor].CGColor);
            CGContextSetLineWidth(context, 5.0);
            CGContextStrokeRect(context, scaledBoundingBox);
        }

        CGRect scaledValidThruBoundingBox = [self dividedRect:cardInfo.validThruBoundingBox
                                                        scale:[UIScreen mainScreen].scale];
        // 유효 기간의 인식 영역을 그린다.                                                  
        CGContextSetStrokeColorWithColor(context, [UIColor orangeColor].CGColor);
        CGContextSetLineWidth(context, 5.0);
        CGContextStrokeRect(context, scaledValidThruBoundingBox);
        
        UIImage *newImage = UIGraphicsGetImageFromCurrentImageContext();
        UIGraphicsEndImageContext();

        imageView.image = newImage;
                
        [self.view addSubview:imageView];
    }
}

- (CGRect)dividedRect:(CGRect)rect
                scale:(CGFloat)scale {
    return CGRectMake(rect.origin.x / scale, rect.origin.y / scale,
                      rect.size.width / scale, rect.size.height / scale);
}

```

#### 초기화 과정 예

```objc
#import <NHNCloudOCR/NHNCloudOCR.h>

@interface ViewController () <NHNCloudCreditCardRecognizerDelegate>
@end

@implementation ViewController

- (void)initializeOCR {
    // 초기화 및 Delegate 설정
    NHNCloudOCRConfiguration *configuration = [NHNCloudOCRConfiguration configurationWithAppKey:@"{AppKey}" secret:@"{Secret}"];

    // 검출 이미지 반환 설정 
    [NHNCloudOCR setDetectedImageReturn:YES];

    // 초기화    
    [NHNCloudOCR initWithConfiguration:configuration];

    // Delegate 설정
    [NHNCloudOCR setCreditCardRecognizerDelegate:self];
}

// 신용카드 인식 결과 반환
- (void)didDetectCreditCardInfo:(nullable NHNCloudCreditCardInfo *)cardInfo error:(nullable NSError *)error {
    NSLog(@"didDetectCreditCardInfo : cardInfo : %@", cardInfo);
    NSLog(@"didDetectCreditCardInfo : error : %@", error);
}

// 스크린 캡처 이벤트 수신
- (void)didDetectCreditCardSecurityEvent:(NHNCloudSecurityEvent)event {

    // 스크린 캡처 경고 Alert 출력 예시
    if (event == NHNCloudSecurityEventScreenshot || event == NHNCloudSecurityEventScreenRecordingOn) {
        UIAlertController *alert = [UIAlertController alertControllerWithTitle:nil message:@"캡처가 감지되었습니다." preferredStyle:UIAlertControllerStyleAlert];
        [alert addAction:[UIAlertAction actionWithTitle:@"OK" style:UIAlertActionStyleDefault handler:nil]];
        
        [self presentViewController:alert animated:YES completion:nil];
    }
    
    // 동영상 녹화 시 빈 화면 출력 예시
    if (event == NHNCloudSecurityEventScreenRecordingOn || event == NHNCloudSecurityEventScreenRecordingOff) {
        if ([[UIScreen mainScreen] isCaptured] ) {
            [[[UIApplication sharedApplication] windows] firstObject].hidden = YES;
        } else {
            [[[UIApplication sharedApplication] windows] firstObject].hidden = NO;
        }
    }
}


// 확인 버튼 이벤트 수신(NHNCloudCreditCardRecognizerViewController 상속 구현 시에만 수신 가능)
- (void)creditCardRecognizerViewControllerConfirm {
    // 신용카드 인식 결과 화면에서 확인 버튼을 눌렀을 때의 처리
}

// 닫기 버튼 이벤트 수신(NHNCloudCreditCardRecognizerViewController 상속 구현 시에만 수신 가능)
- (void)creditCardRecognizerViewControllerCancel {
    // 신용카드 인식 또는 결과 화면에서 닫기 버튼을 눌렀을 때의 처리
}

@end
```

### Credit Card 적용 방법

#### NHNCloudCreditCardRecognizerViewController

**1. Credit-Card Recognizer ViewController 사용하기**

* NHNCloudCreditCardRecognizerViewController를 상속 구현한 Class를 Storyboard의 ViewController에 연결하여 기본 UI가 적용된 Credit-Card Recognizer를 손쉽게 사용할 수 있습니다.

**2. Class 생성**

![default\_viewcontroller](https://static.toastoven.net/toastcloud/sdk/ios/default\_viewcontroller.png)

* NHNCloudCreditCardRecognizerViewController를 subclass로 가지는 ViewController Class를 생성합니다.

**3. Storyboard에 연결**

![create\_viewcontroller](https://static.toastoven.net/toastcloud/sdk/ios/create\_viewcontroller.png)

* Storyboard에 ViewController를 추가합니다.

![custom\_class](https://static.toastoven.net/toastcloud/sdk/ios/custom\_class.png)

* 추가한 ViewController에 Custom Class에 생성한 Class를 설정합니다.

![segue\_viewcontroller](https://static.toastoven.net/toastcloud/sdk/ios/segue\_viewcontroller.png)

* ViewController Segue Event를 설정합니다.
* Delegate를 설정하고 구현합니다.

#### NHNCloudCreditCardRecognizerServiceViewController 커스터마이징

* NHNCloudCreditCardRecognizerServiceViewController를 사용하여 UI를 커스터마이징할 수 있습니다.
  * **Credit-Card 가이드의 경우 미리 정의된 값을 사용하기 때문에 변경이 불가능합니다.**

**1. NHNCloudCreditCardRecognizerServiceViewController 상속**

* NHNCloudCreditCardRecognizerServiceViewController를 상속 구현하여 커스터마이징할 수 있습니다.

**Override 함수 명세**

```objc

// 뷰가 메모리에 만들어질 때 초기 설정 및 데이터 준비 작업을 수행
- (void)viewDidLoad;

// 뷰가 화면에 나타나기 직전에 마지막 작업을 수행
- (void)viewWillAppear:(BOOL)animated;

// 뷰가 화면에서 사라지기 직전에 정리 작업을 수행
- (void)viewWillDisappear:(BOOL)animated;

// 뷰가 화면에서 완전히 사라진 후 추가적인 정리 작업을 수행
- (void)viewDidDisappear:(BOOL)animated;

// Custom UI 갱신
- (void)didUpdateCreditCardGuide:(CGRect)rect orientation:(NHNCloudCreditCardOrientation)orientation;

// 신용카드 인식 시 UI 갱신
- (void)imageDidDetect:(BOOL)detected;
```

**Override 사용 예**

```objc

@interface OCRViewController : NHNCloudCreditCardRecognizerServiceViewController <NHNCloudCreditCardRecognizerDelegate>

@end

@implementation OCRViewController

- (void)viewDidLoad {
    [super viewDidLoad];
    
    [NHNCloudOCR setCreditCardRecognizerDelegate:self];
    // Custom UI 생성
}

- (void)viewWillAppear:(BOOL)animated {
    [super viewWillAppear:animated];
    
    [self startRunning];
}

- (void)viewWillDisappear:(BOOL)animated {
    [super viewWillDisappear:animated];
}

- (void)viewDidDisappear:(BOOL)animated {
    [super viewDidDisappear:animated];
}

- (void)didUpdateCreditCardGuide:(CGRect)rect orientation:(NHNCloudCreditCardOrientation)orientation {
    [super didUpdateCreditCardGuide:rect orientation:orientation];
    
    // Custom UI 갱신  
}

- (void)imageDidDetect:(BOOL)detected {
    [super imageDidDetect:detected];

    // 신용카드 인식 시 UI 갱신
}

- (void)didDetectCreditCardInfo:(nullable NHNCloudCreditCardInfo *)cardInfo error:(nullable NSError *)error {
    
    NSLog(@"didDetectCreditCardInfo : cardInfo : %@", cardInfo);
    NSLog(@"didDetectCreditCardInfo : error : %@", error);
}

```

#### 테스트 환경 사용하기

* NHNCloudOCR SDK에서 테스트를 위해 제공하는 Credit-Card 가이드를 사용하여 OCR을 테스트할 수 있습니다.
  * 신용카드가 Credit-Card 가이드 안에 존재할 경우 OCR이 시작됩니다.
    * 기본값은 hidden으로 눈에 보이지 않는 가이드가 존재합니다.
    * `enableTestGuide`를 사용하여 테스트용 가이드를 출력할 수 있습니다.

**Credit-Card 가이드 API 명세**

```objc
@interface NHNCloudOCRConfiguration : NSObject
- (void)enableTestGuide;
@end
```

**Credit-Card 가이드 사용 예**

```objc
- (void)initializeOCR {
    // 초기화 및 Delegate 설정
    NHNCloudOCRConfiguration *configuration = [NHNCloudOCRConfiguration configurationWithAppKey:@"{AppKey}" secret:@"{Secret}" ];
    
    [configuration enableTestGuide];

    [NHNCloudOCR initWithConfiguration:configuration];

    [NHNCloudOCR setCreditCardRecognizerDelegate:self];
}
```

### Credit-Card Recognizer ViewController 제어하기

> `Credit Card 적용 방법`을 보고 NHNCloudCreditCardRecognizerViewController 또는 NHNCloudCreditCardRecognizerServiceViewController 상속 구현 필요

#### 1. Credit-Card Recognizer 시작/중지

* Credit-Card Recognizer를 시작하거나 중지합니다.

**Credit-Card Recognizer 시작/중지 API 명세**

```objc
- (void)startRunning;
- (void)stopRunning;
- (BOOL)isRunning;
```

**Credit-Card Recognizer 시작/중지 사용 예**

```objc
- (void)start {
  [self startRunning];
}

// 신용카드 인식 결과 반환
- (void)didDetectCreditCardInfo:(nullable NHNCloudCreditCardInfo *)cardInfo error:(nullable NSError *)error {
    [self stopRunning];
}
```

#### 2. Credit-Card 가이드 회전

* 신용카드의 방향에 맞도록 Credit-Card 가이드를 회전시킬 수 있습니다.

**Credit-Card 가이드 회전 API 명세**

```objc
@property (assign, nonatomic, readonly) CGRect creditCardGuide;
@property (assign, nonatomic, readonly) NHNCloudCreditCardOrientation creditCardGuideOrientation;
- (void)rotateCreditCardGuideOrientation;
```

**Credit-Card 가이드 회전 사용 예**

```objc
typedef NS_ENUM(NSInteger, NHNCloudCreditCardOrientation) {

    NHNCloudCreditCardOrientationPortrait = 0,
    NHNCloudCreditCardOrientationLandscape = 1
};

- (void)rotateButtonAction:(UIButton *)button {

    [self rotateCreditCardGuideOrientation];

    NSLog(@"x: %f y: %f width: %f height: %f", self.creditCardGuide.origin.x,
          self.creditCardGuide.origin.y,
          self.creditCardGuide.size.width,
          self.creditCardGuide.size.height);

    NSLog(@"creditCardGuideOrientation: %ld", self.creditCardGuideOrientation);
}

```

#### 3. 라이트 활성/비활성

* 디바이스의 카메라 라이트를 활성화하거나 비활성화합니다.

**라이트 활성/비활성 API 명세**

```objc
- (void)enableTorchMode;
- (void)disableTorchMode;
- (BOOL)isEnableTorchMode;
```

**라이트 활성/비활성 사용 예**

```objc
- (void)torchButtonAction:(UIButton *)button {    
    if ([self isEnableTorchMode] == YES) {
        [self disableTorchMode];
    } else {
        [self enableTorchMode];
    }
}

```

#### 4. 카메라 활성/비활성

* 디바이스의 카메라를 활성화하거나 비활성화합니다.

**카메라 활성/비활성 API 명세**

```objc
- (void)startRunningCamera;
- (void)stopRunningCamera;
- (BOOL)isRunnginCamera;
```

**카메라 활성/비활성 사용 예**

```objc
- (void)cameraButtonAction:(UIButton *)button {    
    if ([self isRunnginCamera] == YES) {
        [self stopRunningCamera];
    } else {
        [self startRunningCamera];
    }
}

```
