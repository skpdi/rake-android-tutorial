# Change Log

## 0.7.0 (2019-07-24)

**Changed**
- dmp mode 추가(dmpc field에 google advertisingId 자동삽입)
- 국내/국외 Endpoint URL 자동 설정기능 제거

## 0.6.4 (2019-04-24)

**Changed**
- 내부 metric 전송 로직 변경

## 0.6.3 (2018-12-03)

**Changed**
- rake SDK token 저장 방식 변경

## 0.6.2 (2018-11-05)

**Changed**
- track() 함수 실행 속도 개선 : track() 1회 실행시 기존 10~20ms 에서 0~1ms로 개선

**Added**
- 신규 API excludeAutoProperties() 제공 : 자동 수집 필드 중, 사용자가 수집을 원하지 않는 필드를 제외

```
RakeAPI rake = RakeAPI.getInstance(getApplicationContext(), "your-rake-token", RakeAPI.Env.Live, RakeAPI.Logging.DISABLE);
// 자동수집 예외 필드명을 배열로 추가
// 배열 형태로 여러개 등록 가능하며, 여러번 호출시 기존 예외처리 항목에 덮어씌움.
// track() 호출 전 아래와 같이 미리 등록할 경우, 등록된 항목들을 자동수집 하지 않음
rake.excludeAutoProperties(new String[]{"device_id"});
...
rake.track(shuttle.toJSONObject());
...
// 자동수집 예외 필드명 reset
// 해당 함수에 null 또는 빈 배열 전달시 기본 자동수집 항목 수집
rake.excludeAutoProperties(null);
```

## 0.6.1 (2018-08-14)

**Fixed**
- 2개 이상의 Rake Token 사용시 (RakeAPI 인스턴스를 2개 이상 만들어 사용시) 로그가 중복 전송되는 이슈 수정

## 0.6.0 (2018-07-26)

**Changed**
- track() 함수 실행 속도 개선 : track() 1회 실행시 기존 10~20ms 에서 0~1ms로 개선

**Added**
- 신규 API excludeAutoProperties() 제공 : 자동 수집 필드 중, 사용자가 수집을 원하지 않는 필드를 제외

```
RakeAPI rake = RakeAPI.getInstance(getApplicationContext(), "your-rake-token", RakeAPI.Env.Live, RakeAPI.Logging.DISABLE);
// 자동수집 예외 필드명을 배열로 추가
// 배열 형태로 여러개 등록 가능하며, 여러번 호출시 기존 예외처리 항목에 덮어씌움.
// track() 호출 전 아래와 같이 미리 등록할 경우, 등록된 항목들을 자동수집 하지 않음
rake.excludeAutoProperties(new String[]{"device_id"});
...
rake.track(shuttle.toJSONObject());
...
// 자동수집 예외 필드명 reset
// 해당 함수에 null 또는 빈 배열 전달시 기본 자동수집 항목 수집
rake.excludeAutoProperties(null);
```

## 0.5.1 (2018-05-04)

**Changed**
- DB Transaction 이후 결과값 리턴시 간헐적인 NullPointException 발생 예외처리
- 런타임 업그레이드
  - kotiln version up to 1.2.30
  - gradle version up to 3.1.1
  - build tool version up to 27.0.3

## 0.5.0(2018-01-22)

**Changed**
- minSdkVersion 변경 : Ice Cream Sandwich (Android 4.0, API Level 14) 이상 지원
- 코드 리팩토링
- 자체 Metric 로그 수집용 셔틀 라이브러리 교체

## 0.4.8 (2017-07-20)

**Changed**
- Shuttle에 필드(app_version, app_release, app_build_number)가 존재할 경우 자동 수집되며, app_version은 신규 프로젝트의 로그 정의서 및 shuttle에서는 빠질 예정. (이미 입수중인 프로젝트에서는 수집)

**Fixed**
- Debug Build시 app_version에 Build Date 값을 붙였으나, 안드로이드 버전업이 됨에 따라 해당 값이 정상 출력되지 않으므로 제거.
- Android O VM Policy 강화에 따라 StrictMode 사용시 로그 전송 실패에 대한 예외처리 추가.

## 0.4.7 (2017-05-31)

**Changed**
- 라이브러리 배포 편의성 개선 : RakeAPI 인스턴스 생성시 국내/국외 Endpoint URL 자동 설정 
- Code Refactoring을 통한 jar 파일 사이즈 감소 (101KB > 93KB)
- SDK minSdkVersion 변경(API Level 8 -> API Level 9): Gingerbread(Android 2.3) 이상 지원
- Apache Http Client 라이브러리 제거. 모든 네트워트 작업을 HttpURLConnection으로 통일

**Added**
- Library version check API 추가
- API Desc. : public static String getLibVersion()

```
String libVersion = RakeAPI.getLibVersion()
```

## 0.4.6 (2017-03-03)

**Added**
- RakeAPI 클래스에 상기 변경사항이 반영된 API 추가
- API Desc. : public void setServerPort(int port)

```
RakeAPI rake = RakeAPI.getInstance(getApplicationContext(), "your-rake-token", RakeAPI.Env.Live, RakeAPI.Logging.DISABLE);
rake.setServerPort(1234);
```


## 0.4.5 (2017-02-16)

**Changed**
- Android 6.0 이상 단말부터 적용된 Doze Mode 관련 예외처리

## Lower version changelog
더 낮은 버젼의 SDK change log는 Maintainer에게 문의하세요

## Change log template
- Added : 새로운 기능
- Changed : 기존 기능의 변경사항
- Deprecated : 곧 지워질 기능
- Removed : 지금 지워진 기능
- Fixed : 버그 픽스
- Security : 취약점이 있는 경우