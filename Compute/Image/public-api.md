# API 가이드

### Compute > Image > API v2 가이드

API를 사용하려면 API 엔드포인트와 토큰 등이 필요합니다. [API 사용 준비](../Compute/ko/identity-api/)를 참고하여 API 사용에 필요한 정보를 준비합니다.

이미지 API는 `image` 타입 엔드포인트를 이용합니다. 정확한 엔드포인트는 토큰 발급 응답의 `serviceCatalog`를 참조합니다.

| 타입    | 리전                                     | 엔드포인트                                                                                                                                                                                   |
| ----- | -------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| image | <p>한국(판교) 리전<br>한국(평촌) 리전<br>일본 리전</p> | <p>https://kr1-api-image-infrastructure.nhncloudservice.com<br>https://kr2-api-image-infrastructure.nhncloudservice.com<br>https://jp1-api-image-infrastructure.nhncloudservice.com</p> |

API 응답에 가이드에 명시되지 않은 필드가 나타날 수 있습니다. 이런 필드는 NHN Cloud 내부 용도로 사용되며 사전 공지 없이 변경될 수 있으므로 사용하지 않습니다.

### 이미지

#### 이미지 목록 조회

```
GET /v2/images
X-Auth-Token: {tokenId}
```

**요청**

이 API는 요청 본문을 요구하지 않습니다.

| 이름                | 종류     | 형식      | 필수 | 설명                                                                                                                                                                                                                                |
| ----------------- | ------ | ------- | -- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| tokenId           | Header | String  | O  | 토큰 ID                                                                                                                                                                                                                             |
| limit             | Query  | Integer | -  | 반환할 이미지 개수(기본값은 25)                                                                                                                                                                                                               |
| marker            | Query  | UUID    | -  | <p>조회할 이미지 목록의 첫 번째 이미지 ID<br>정렬 방식에 따라 <code>marker</code>로 지정된 이미지부터 <code>limit</code>만큼의 이미지 목록을 조회</p>                                                                                                                       |
| name              | Query  | String  | -  | 조회할 이미지 이름                                                                                                                                                                                                                        |
| visibility        | Query  | Enum    | -  | <p>조회할 이미지의 보여 주기 속성<br><code>public</code>, <code>private</code>, <code>shared</code> 중 하나의 값만 선택 가능<br>생략하면 모든 종류의 이미지 목록 반환</p>                                                                                                |
| owner             | Query  | String  | -  | 조회할 이미지가 속한 테넌트 ID                                                                                                                                                                                                                |
| status            | Query  | Enum    | -  | <p>조회할 이미지 상태<br><code>queued</code>: 이미지 변환 중<br><code>saving</code>: 이미지 업로드 중<br><code>active</code>: 정상<br><code>killed</code>: 시스템에서 이미지 삭제<br><code>deleted</code>: 삭제된 이미지<br><code>pending_delete</code>: 이미지 삭제 대기 중</p> |
| size\_min         | Query  | Integer | -  | 조회할 이미지의 최소 크기(바이트)                                                                                                                                                                                                               |
| size\_max         | Query  | Integer | -  | 조회할 이미지의 최대 크기(바이트)                                                                                                                                                                                                               |
| nhncloud\_product | Query  | Enum    | -  | <p>조회할 이미지의 인프라 서비스 종류<br><code>compute</code>: Instance 서비스 이미지<br><code>gpu</code>: GPU Instance 서비스 이미지</p>                                                                                                                    |
| sort\_key         | Query  | String  | -  | <p>이미지 목록을 정렬할 때 사용할 속성<br>이미지의 모든 속성을 지정 가능, 기본값은 <code>created_at</code></p>                                                                                                                                                    |
| sort\_dir         | Query  | Enum    | -  | <p>이미지 목록 정렬 방향<br><code>asc</code>(오름차순), <code>desc</code>(내림차순) 중 하나의 값만 선택 가능, 기본값은 내림차순</p>                                                                                                                                  |

**응답**

| 이름                       | 종류   | 형식       | 설명                                                                                                                                                          |
| ------------------------ | ---- | -------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| images                   | Body | Array    | 이미지 목록 객체                                                                                                                                                   |
| images.status            | Body | String   | <p>이미지 상태<br><code>queued</code>, <code>saving</code>, <code>active</code>, <code>killed</code>, <code>deleted</code>, <code>pending_delete</code> 중 하나</p> |
| images.name              | Body | String   | 이미지 이름                                                                                                                                                      |
| images.tags              | Body | Array    | <p>이미지 태그 목록<br><code>_AVAILABLE_</code> 태그를 삭제하면 콘솔에서는 조회되지 않으므로, 태그를 삭제하지 않도록 주의</p>                                                                      |
| images.container\_format | Body | String   | 이미지 컨테이너 포맷                                                                                                                                                 |
| images.created\_at       | Body | Datetime | 생성 시각                                                                                                                                                       |
| images.disk\_format      | Body | String   | 이미지 디스크 포맷                                                                                                                                                  |
| images.updated\_at       | Body | Datetime | 수정 시각                                                                                                                                                       |
| images.min\_disk         | Body | Integer  | <p>이미지 최소 디스크 요구량(GB)<br><code>min_disk</code> 값보다 큰 블록 스토리지에서만 사용할 수 있음</p>                                                                                |
| images.protected         | Body | Boolean  | <p>이미지 보호 여부<br><code>protected=true</code>인 경우 수정 및 삭제 불가</p>                                                                                              |
| images.id                | Body | UUID     | 이미지 ID                                                                                                                                                      |
| images.min\_ram          | Body | Integer  | <p>이미지 최소 메모리 요구량(MB)<br><code>min_disk</code> 값보다 큰 인스턴스에서만 사용할 수 있음</p>                                                                                   |
| images.checksum          | Body | String   | <p>이미지 내용 해시값<br>내부적으로 이미지 유효성 검증을 위해 사용</p>                                                                                                                |
| images.owner             | Body | String   | 이미지가 속한 테넌트 ID                                                                                                                                              |
| images.visibility        | Body | Enum     | <p>이미지 가시성<br><code>public</code>, <code>private</code>, <code>shared</code> 중 하나</p>                                                                       |
| images.virtual\_size     | Body | Integer  | 이미지 가상 크기                                                                                                                                                   |
| images.size              | Body | Integer  | 이미지 실제 크기(바이트)                                                                                                                                              |
| images.properties        | Body | Object   | <p>이미지 속성 객체<br>이미지별 사용자 지정 속성을 키-값 쌍 형태로 기술</p>                                                                                                            |
| images.self              | Body | URI      | 이미지 경로                                                                                                                                                      |
| images.file              | Body | String   | 이미지 파일 경로                                                                                                                                                   |
| images.schema            | Body | URI      | 이미지 스키마 경로                                                                                                                                                  |
| schema                   | Body | URI      | 이미지 목록 스키마 경로                                                                                                                                               |
| first                    | Body | URI      | 이미지 목록의 첫 번째 페이지에 해당하는 경로                                                                                                                                   |
| next                     | Body | URI      | 이미지 목록의 다음 페이지에 해당하는 경로                                                                                                                                     |

<details>

<summary>예시</summary>

```json
{
  "images": [
    {
      "container_format": "bare",
      "min_ram": 0,
      "updated_at": "2018-12-11T01:01:35Z",
      "login_username": "centos",
      "file": "/v2/images/1c868787-6207-4ff2-a1e7-ae1331d6829b/file",
      "owner": "c289b99209ca4e189095cdecebbd092d",
      "id": "1c868787-6207-4ff2-a1e7-ae1331d6829b",
      "size": 1778843648,
      "os_distro": "CentOS",
      "self": "/v2/images/1c868787-6207-4ff2-a1e7-ae1331d6829b",
      "disk_format": "qcow2",
      "os_version": "6.10",
      "schema": "/v2/schemas/image",
      "status": "active",
      "description": "CentOS 6.10 (2018.10.23)",
      "tags": [],
      "visibility": "public",
      "os_architecture": "amd64",
      "min_disk": 20,
      "virtual_size": null,
      "name": "CentOS 6.10 (2018.10.23)",
      "hypervisor_type": "qemu",
      "created_at": "2018-10-23T02:17:43Z",
      "protected": true,
      "checksum": "f803c5c15bcf9a75935980a900a04584",
      "os_type": "linux"
    }
  ],
  "schema": "/v2/schemas/images",
  "first": "/v2/images",
  "next": "/v2/images?marker=057f9a69-4e4c-4025-8a69-fa248cd9db94"
}
```

</details>

***

#### 이미지 보기

```
GET /v2/images/{imageId}
X-Auth-Token: {tokenId}
```

**요청**

이 API는 요청 본문을 요구하지 않습니다.

| 이름      | 종류     | 형식     | 필수 | 설명         |
| ------- | ------ | ------ | -- | ---------- |
| imageId | URL    | UUID   | O  | 조회할 이미지 ID |
| tokenId | Header | String | O  | 토큰 ID      |

**응답**

| 이름                | 종류   | 형식       | 설명                                                                                     |
| ----------------- | ---- | -------- | -------------------------------------------------------------------------------------- |
| status            | Body | String   | 이미지 상태                                                                                 |
| name              | Body | String   | 이미지 이름                                                                                 |
| tags              | Body | String   | <p>이미지 태그 목록<br><code>_AVAILABLE_</code> 태그를 삭제하면 콘솔에서는 조회되지 않으므로, 태그를 삭제하지 않도록 주의</p> |
| container\_format | Body | String   | 이미지 컨테이너 포맷                                                                            |
| created\_at       | Body | Datetime | 생성 시각                                                                                  |
| disk\_format      | Body | String   | 이미지 디스크 포맷                                                                             |
| updated\_at       | Body | Datetime | 수정 시각                                                                                  |
| min\_disk         | Body | Integer  | <p>이미지 최소 디스크 요구량(GB)<br><code>min_disk</code> 값보다 큰 블록 스토리지에서만 사용할 수 있음</p>           |
| protected         | Body | Boolean  | <p>이미지 보호 여부<br><code>protected=true</code>인 경우 수정 및 삭제 불가</p>                         |
| id                | Body | UUID     | 이미지 ID                                                                                 |
| min\_ram          | Body | Integer  | <p>이미지 최소 메모리 요구량(MB)<br><code>min_disk</code> 값보다 큰 인스턴스에서만 사용할 수 있음</p>              |
| checksum          | Body | String   | <p>이미지 내용의 해시값<br>내부적으로 이미지 유효성 검증을 위해 사용</p>                                          |
| owner             | Body | String   | 이미지가 속한 테넌트 ID                                                                         |
| visibility        | Body | Enum     | <p>이미지 가시성<br><code>public</code>, <code>private</code>, <code>shared</code> 중 하나</p>  |
| virtual\_size     | Body | Integer  | 이미지 가상 크기                                                                              |
| size              | Body | Integer  | 이미지 실제 크기(바이트)                                                                         |
| properties        | Body | Object   | <p>이미지 속성 객체<br>이미지별 사용자 지정 속성을 키-값 쌍 형태로 기술</p>                                       |
| self              | Body | URI      | 이미지 경로                                                                                 |
| file              | Body | String   | 이미지 파일 경로                                                                              |
| schema            | Body | URI      | 이미지 스키마 경로                                                                             |

<details>

<summary>예시</summary>

```json
{
  "container_format": "bare",
  "min_ram": 0,
  "updated_at": "2018-12-11T01:01:35Z",
  "login_username": "centos",
  "file": "/v2/images/1c868787-6207-4ff2-a1e7-ae1331d6829b/file",
  "owner": "c289b99209ca4e189095cdecebbd092d",
  "id": "1c868787-6207-4ff2-a1e7-ae1331d6829b",
  "size": 1778843648,
  "os_distro": "CentOS",
  "self": "/v2/images/1c868787-6207-4ff2-a1e7-ae1331d6829b",
  "disk_format": "qcow2",
  "os_version": "6.10",
  "schema": "/v2/schemas/image",
  "status": "active",
  "description": "CentOS 6.10 (2018.10.23)",
  "tags": [],
  "visibility": "public",
  "os_architecture": "amd64",
  "min_disk": 20,
  "virtual_size": null,
  "name": "CentOS 6.10 (2018.10.23)",
  "hypervisor_type": "qemu",
  "created_at": "2018-10-23T02:17:43Z",
  "protected": true,
  "checksum": "f803c5c15bcf9a75935980a900a04584",
  "os_type": "linux"
}
```

</details>

***

#### 이미지 생성

```
POST /v2/images
X-Auth-Token: {tokenId}
```

**요청**

| 이름                | 종류     | 형식      | 필수 | 설명                                                                                     |
| ----------------- | ------ | ------- | -- | -------------------------------------------------------------------------------------- |
| tokenId           | Header | String  | O  | 토큰 ID                                                                                  |
| container\_format | Body   | String  | -  | 이미지 컨테이너 포맷                                                                            |
| disk\_format      | Body   | String  | -  | 이미지 디스크 포맷                                                                             |
| min\_disk         | Body   | Integer | -  | 이미지 최소 디스크 요구량(GB)                                                                     |
| min\_ram          | Body   | Integer | -  | 이미지 최소 메모리 요구량(MB)                                                                     |
| protected         | Body   | Boolean | -  | 이미지 보호 여부, true 또는 false                                                               |
| tags              | Body   | Array   | -  | <p>이미지 태그 목록<br><code>_AVAILABLE_</code> 태그를 삭제하면 콘솔에서는 조회되지 않으므로, 태그를 삭제하지 않도록 주의</p> |
| visibility        | Body   | String  | -  | <p>이미지 가시성<br><code>public</code>, <code>private</code>, <code>shared</code> 중 하나</p>  |

<details>

<summary>예시</summary>

```json
{
    "container_format": "bare",
    "disk_format": "raw",
    "name": "Ubuntu",
}
```

</details>

**응답**

| 이름                | 종류   | 형식       | 설명                                                                                                                                                          |
| ----------------- | ---- | -------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| status            | Body | String   | <p>이미지 상태<br><code>queued</code>, <code>saving</code>, <code>active</code>, <code>killed</code>, <code>deleted</code>, <code>pending_delete</code> 중 하나</p> |
| name              | Body | String   | 이미지 이름                                                                                                                                                      |
| tags              | Body | String   | <p>이미지 태그 목록<br><code>_AVAILABLE_</code> 태그를 삭제하면 콘솔에서는 조회되지 않으므로, 태그를 삭제하지 않도록 주의</p>                                                                      |
| container\_format | Body | String   | 이미지 컨테이너 포맷                                                                                                                                                 |
| created\_at       | Body | Datetime | 생성 시각                                                                                                                                                       |
| disk\_format      | Body | String   | 이미지 디스크 포맷                                                                                                                                                  |
| updated\_at       | Body | Datetime | 수정 시각                                                                                                                                                       |
| min\_disk         | Body | Integer  | <p>이미지 최소 디스크 요구량(GB)<br><code>min_disk</code> 값보다 큰 블록 스토리지에서만 사용할 수 있음</p>                                                                                |
| protected         | Body | Boolean  | <p>이미지 보호 여부<br><code>protected=true</code>인 경우 수정 및 삭제 불가</p>                                                                                              |
| id                | Body | UUID     | 이미지 ID                                                                                                                                                      |
| min\_ram          | Body | Integer  | <p>이미지 최소 메모리 요구량(MB)<br><code>min_disk</code> 값보다 큰 인스턴스에서만 사용할 수 있음</p>                                                                                   |
| checksum          | Body | String   | <p>이미지 내용의 해시값<br>내부적으로 이미지 유효성 검증을 위해 사용</p>                                                                                                               |
| owner             | Body | String   | 이미지가 속한 테넌트 ID                                                                                                                                              |
| visibility        | Body | Enum     | <p>이미지 가시성<br><code>public</code>, <code>private</code>, <code>shared</code> 중 하나</p>                                                                       |
| virtual\_size     | Body | Integer  | 이미지 가상 크기                                                                                                                                                   |
| size              | Body | Integer  | 이미지 실제 크기(바이트)                                                                                                                                              |
| properties        | Body | Object   | <p>이미지 속성 객체<br>이미지별 사용자 지정 속성을 키-값 쌍 형태로 기술</p>                                                                                                            |
| self              | Body | URI      | 이미지 경로                                                                                                                                                      |
| file              | Body | String   | 이미지 파일 경로                                                                                                                                                   |
| schema            | Body | URI      | 이미지 스키마 경로                                                                                                                                                  |

<details>

<summary>예시</summary>

```json
{
    "status": "queued",
    "name": "Ubuntu",
    "tags": [],
    "container_format": "bare",
    "created_at": "2015-11-29T22:21:42Z",
    "size": null,
    "disk_format": "raw",
    "updated_at": "2015-11-29T22:21:42Z",
    "visibility": "private",
    "locations": [],
    "self": "/v2/images/b2173dd3-7ad6-4362-baa6-a68bce3565cb",
    "min_disk": 0,
    "protected": false,
    "id": "b2173dd3-7ad6-4362-baa6-a68bce3565cb",
    "file": "/v2/images/b2173dd3-7ad6-4362-baa6-a68bce3565cb/file",
    "checksum": null,
    "os_hash_algo": null,
    "os_hash_value": null,
    "os_hidden": false,
    "owner": "bab7d5c60cd041a0a36f7c4b6e1dd978",
    "virtual_size": null,
    "min_ram": 0,
    "schema": "/v2/schemas/image"
}
```

</details>

***

#### 이미지 업로드

지정한 이미지에 실제 이미지 파일을 업로드합니다.

```
PUT /v2/images/{imageId}/file
X-Auth-Token: {tokenId}
Content-Type: application/octet-stream
```

**요청**

요청 시 Header의 Content-Type을 application/octet-stream으로 설정해야 합니다.

| 이름      | 종류     | 형식     | 필수 | 설명                    |
| ------- | ------ | ------ | -- | --------------------- |
| imageId | URL    | UUID   | O  | 이미지 ID                |
| tokenId | Header | String | O  | 토큰 ID                 |
| -       | Body   | Binary | O  | 업로드할 이미지 파일의 바이너리 데이터 |

**응답**

이 API는 응답 본문을 반환하지 않습니다. 요청이 올바르면 상태 코드 204를 반환합니다.

***

#### 이미지 다운로드

지정한 이미지의 바이너리 데이터를 다운로드합니다.

```
GET /v2/images/{imageId}/file
X-Auth-Token: {tokenId}
```

**요청**

| 이름      | 종류     | 형식     | 필수 | 설명     |
| ------- | ------ | ------ | -- | ------ |
| imageId | URL    | UUID   | O  | 이미지 ID |
| tokenId | Header | String | O  | 토큰 ID  |

**응답**

이미지의 바이너리 데이터가 반환됩니다. 요청이 올바르면 상태 코드 200을 반환합니다.

***

#### 이미지 수정

이미지 수정을 통해 이미지 속성을 변경할 수 있습니다.

```
PATCH /v2/images/{imageId}
X-Auth-Token: {tokenId}
Content-Type: application/openstack-images-v2.1-json-patch
```

**요청**

요청 시 Header의 Content-Type을 application/openstack-images-v2.1-json-patch로 설정해야 합니다.

| 이름      | 종류     | 형식     | 필수 | 설명                                                                                                         |
| ------- | ------ | ------ | -- | ---------------------------------------------------------------------------------------------------------- |
| imageId | URL    | UUID   | O  | 수정할 이미지 ID                                                                                                 |
| tokenId | Header | String | O  | 토큰 ID                                                                                                      |
| op      | Body   | Enum   | O  | <p>수정할 작업 유형<br><code>add</code>: 속성 추가<br><code>replace</code>: 속성 값 수정<br><code>remove</code>: 속성 삭제</p> |
| path    | Body   | String | O  | <p>수정할 속성<br><code>/{path}</code> 형식</p>                                                                   |
| value   | Body   | String | -  | 수정할 속성의 값                                                                                                  |

<details>

<summary>예시</summary>

```json
// 속성 추가
[
    {
        "op": "add",
        "path": "/metadata1",
        "value": "value1"
    },
    {
        "op": "add",
        "path": "/metadata2",
        "value": "1"
    }
]

// 속성 값 수정
[
    {
        "op": "replace",
        "path": "/metadata1",
        "value": "value2"
    }
]

// 속성 삭제
[
    {
        "op": "remove",
        "path": "/metadata1"
    }
]
```

</details>

**응답**

이미지 보기와 동일한 응답을 반환합니다.

***

#### 이미지 삭제

가시성이 `public`인 이미지는 삭제할 수 없습니다.

```
DELETE /v2/images/{imageId}
X-Auth-Token: {tokenId}
```

**요청**

이 API는 요청 본문을 요구하지 않습니다.

| 이름      | 종류     | 형식     | 필수 | 설명         |
| ------- | ------ | ------ | -- | ---------- |
| imageId | URL    | String | O  | 삭제할 이미지 ID |
| tokenId | Header | String | O  | 토큰 ID      |

**응답**

이 API는 응답 본문을 반환하지 않습니다.

***

### 이미지 태그

#### 태그 추가하기

지정한 이미지에 태그를 추가합니다.

```
PUT /v2/images/{imageId}/tags/{tag}
X-Auth-Token: {tokenId}
```

**요청**

이 API는 요청 본문을 요구하지 않습니다.

| 이름      | 종류     | 형식     | 필수 | 설명                                                                                           |
| ------- | ------ | ------ | -- | -------------------------------------------------------------------------------------------- |
| imageId | URL    | UUID   | O  | 태그를 추가할 이미지 ID                                                                               |
| tag     | URL    | String | O  | <p>추가할 태그 이름(영문 기준 최대 255자)<br><strong>(주의) <code>_</code>로 시작하는 태그는 사용할 수 없습니다</strong></p> |
| tokenId | Header | String | O  | 토큰 ID                                                                                        |

**응답**

이 API는 응답 본문을 반환하지 않습니다.

***

#### 태그 제거하기

지정한 이미지에서 태그를 제거합니다.

```
DELETE /v2/images/{imageId}/tags/{tag}
X-Auth-Token: {tokenId}
```

**요청**

이 API는 요청 본문을 요구하지 않습니다.

| 이름      | 종류     | 형식     | 필수 | 설명             |
| ------- | ------ | ------ | -- | -------------- |
| imageId | URL    | UUID   | O  | 태그를 제거할 이미지 ID |
| tag     | URL    | String | O  | 제거할 태그 이름      |
| tokenId | Header | String | O  | 토큰 ID          |

**응답**

이 API는 응답 본문을 반환하지 않습니다.

***

### 이미지 공유

이미지 공유를 통해 자신의 테넌트에 소속된 이미지를 다른 테넌트에 공유할 수 있습니다. 이미지 공유 방법은 다음과 같습니다.

1. 이미지 가시성을 `shared`로 변경합니다.
2. 공유받을 테넌트를 이미지의 멤버로 등록합니다.

공유한 이미지는 공유받은 테넌트에서 바로 사용할 수 있지만 이미지 목록 조회에서는 표시되지 않습니다. **공유받은 테넌트**에서 멤버 상태를 `active`로 변경하면 공유받은 이미지가 조회됩니다.

#### 가시성 변경

```
PATCH /v2/images/{imageId}
X-Auth-Token: {tokenId}
Content-Type: application/openstack-images-v2.1-json-patch
```

**요청**

| 이름      | 종류     | 형식     | 필수 | 설명                              |
| ------- | ------ | ------ | -- | ------------------------------- |
| imageId | URL    | UUID   | O  | 공유할 이미지 ID                      |
| tokenId | Header | String | O  | 토큰 ID                           |
| op      | Body   | String | O  | `replace`로 지정                   |
| path    | Body   | String | O  | `/visibility`로 지정               |
| value   | Body   | String | O  | 변경할 가시성값, `private` 또는 `shared` |

<details>

<summary>예시</summary>

```json
[
    {
        "op" : "replace",
        "path" : "/visibility",
        "value" : "shared"
    }
]
```

</details>

**응답**

이미지 보기와 동일한 응답을 반환합니다.

***

#### 멤버 추가

공유받을 테넌트를 지정한 이미지의 멤버로 등록합니다.

```
POST /v2/images/{imageId}/members
X-Auth-Token: {tokenId}
```

**요청**

| 이름      | 종류     | 형식     | 필수 | 설명          |
| ------- | ------ | ------ | -- | ----------- |
| imageId | URL    | UUID   | O  | 공유할 이미지 ID  |
| tokenId | Header | String | O  | 토큰 ID       |
| member  | Body   | String | O  | 공유받을 테넌트 ID |

<details>

<summary>예시</summary>

```
{
    "member": "8989447062e04a818baf9e073fd04fa7"
}
```

</details>

**응답**

| 이름          | 종류   | 형식       | 설명                                                                   |
| ----------- | ---- | -------- | -------------------------------------------------------------------- |
| created\_at | Body | Datetime | <p>멤버 생성 시각<br><code>YYYY-MM-DDThh:mm:ssZ</code> 형식</p>              |
| image\_id   | Body | UUID     | 공유한 이미지 ID                                                           |
| member\_id  | Body | String   | 이미지를 공유받은 테넌트 ID                                                     |
| schema      | Body | URI      | 이미지 멤버에 대한 스키마 경로                                                    |
| status      | Body | Enum     | <p>이미지 멤버 상태<br><code>pending</code>, <code>accepted</code> 중 하나</p> |

<details>

<summary>예시</summary>

```json
{
    "created_at": "2013-09-20T19:22:19Z",
    "image_id": "a96be11e-8536-4910-92cb-de50aa19dfe6",
    "member_id": "8989447062e04a818baf9e073fd04fa7",
    "schema": "/v2/schemas/member",
    "status": "pending",
    "updated_at": "2013-09-20T19:25:31Z"
}
```

</details>

***

#### 멤버 목록 보기

지정한 이미지를 공유받은 테넌트 목록을 조회합니다. 반드시 해당 이미지가 소속된 테넌트나 공유받은 테넌트의 토큰으로 요청합니다.

```
GET /v2/images/{imageId}/members
X-Auth-Token: {tokenId}
```

**요청**

이 API는 요청 본문을 요구하지 않습니다.

| 이름      | 종류     | 형식     | 필수 | 설명     |
| ------- | ------ | ------ | -- | ------ |
| imageId | URL    | UUID   | O  | 이미지 ID |
| tokenId | Header | String | O  | 토큰 ID  |

**응답**

| 이름                  | 종류   | 형식       | 설명                                                                   |
| ------------------- | ---- | -------- | -------------------------------------------------------------------- |
| members             | Body | Object   | 멤버 객체 목록                                                             |
| members.created\_at | Body | Datetime | 멤버 생성 시각 `YYYY-MM-DDThh:mm:ssZ` 형식                                   |
| members.image\_id   | Body | UUID     | 공유한 이미지 ID                                                           |
| members.member\_id  | Body | String   | 이미지를 공유받은 테넌트 ID                                                     |
| members.schema      | Body | URI      | 이미지 멤버 스키마 경로                                                        |
| members.status      | Body | Enum     | <p>이미지 멤버 상태<br><code>pending</code>, <code>accepted</code> 중 하나</p> |
| schema              | Body | URI      | 이미지 멤버 목록에 대한 스키마 경로                                                 |

<details>

<summary>예시</summary>

```json
{
    "members": [
        {
            "created_at": "2013-10-07T17:58:03Z",
            "image_id": "dbc999e3-c52f-4200-bedd-3b18fe7f87fe",
            "member_id": "123456789",
            "schema": "/v2/schemas/member",
            "status": "pending",
            "updated_at": "2013-10-07T17:58:03Z"
        },
        {
            "created_at": "2013-10-07T17:58:55Z",
            "image_id": "dbc999e3-c52f-4200-bedd-3b18fe7f87fe",
            "member_id": "987654321",
            "schema": "/v2/schemas/member",
            "status": "accepted",
            "updated_at": "2013-10-08T12:08:55Z"
        }
    ],
    "schema": "/v2/schemas/members"
}
```

</details>

***

#### 멤버 상세 보기

지정한 이미지의 특정 멤버에 대한 상세 정보를 반환합니다. 반드시 해당 이미지가 소속된 테넌트나 공유받은 테넌트의 토큰으로 요청합니다.

```
GET /v2/images/{imageId}/members/{memberId}
X-Auth-Token: {tokenId}
```

**요청**

이 API는 요청 본문을 요구하지 않습니다.

| 이름       | 종류     | 형식     | 필수 | 설명     |
| -------- | ------ | ------ | -- | ------ |
| imageId  | URL    | UUID   | O  | 이미지 ID |
| memberId | URL    | String | O  | 멤버 ID  |
| tokenId  | Header | String | O  | 토큰 ID  |

**응답**

| 이름          | 종류   | 형식       | 설명                                                                   |
| ----------- | ---- | -------- | -------------------------------------------------------------------- |
| created\_at | Body | Datetime | 멤버 생성 시각 `YYYY-MM-DDThh:mm:ssZ` 형식                                   |
| image\_id   | Body | UUID     | 공유한 이미지 ID                                                           |
| member\_id  | Body | String   | 이미지를 공유받은 테넌트 ID                                                     |
| schema      | Body | URI      | 이미지 멤버 스키마 경로                                                        |
| status      | Body | Enum     | <p>이미지 멤버 상태<br><code>pending</code>, <code>accepted</code> 중 하나</p> |

<details>

<summary>예시</summary>

```json
{
    "status": "pending",
    "created_at": "2013-11-26T07:21:21Z",
    "updated_at": "2013-11-26T07:21:21Z",
    "image_id": "0ae74cc5-5147-4239-9ce2-b0c580f7067e",
    "member_id": "8989447062e04a818baf9e073fd04fa7",
    "schema": "/v2/schemas/member"
}
```

</details>

***

#### 멤버 상태 변경

공유받은 테넌트에서 공유받은 이미지를 승인합니다. 이미지 공유를 승인하면 이미지 목록 조회에서도 해당 이미지가 조회됩니다. 반드시 공유받은 테넌트의 토큰으로 요청합니다.

```
PUT /v2/images/{imageId}/members/{memberId}
X-Auth-Token: {tokenId}
```

**요청**

| 이름       | 종류     | 형식     | 필수 | 설명                                     |
| -------- | ------ | ------ | -- | -------------------------------------- |
| imageId  | URL    | UUID   | O  | 이미지 ID                                 |
| memberId | URL    | String | O  | 멤버 ID                                  |
| tokenId  | Header | String | O  | 토큰 ID                                  |
| status   | Body   | Enum   | O  | `accepted`, `pending`, `rejected` 중 하나 |

<details>

<summary>예시</summary>

```json
{
    "status": "accepted"
}
```

</details>

**응답**

| 이름          | 종류   | 유형       | 설명                                                                                        |
| ----------- | ---- | -------- | ----------------------------------------------------------------------------------------- |
| created\_at | Body | Datetime | <p>멤버 생성 시각<br><code>YYYY-MM-DDThh:mm:ssZ</code> 형식</p>                                   |
| image\_id   | Body | UUID     | 공유한 이미지 ID                                                                                |
| member\_id  | Body | String   | 이미지를 공유받은 테넌트 ID                                                                          |
| schema      | Body | URI      | 이미지 멤버 스키마 경로                                                                             |
| status      | Body | Enum     | <p>이미지 멤버 상태<br><code>accpeted</code>,<code>pending</code>,<code>rejected</code> 중 하나</p> |
| updated\_at | Body | Datetime | <p>멤버 상태 수정 시각<br><code>YYYY-MM-DDThh:mm:ssZ</code> 형식</p>                                |

<details>

<summary>예시</summary>

```json
{
    "created_at": "2013-09-20T19:22:19Z",
    "image_id": "a96be11e-8536-4910-92cb-de50aa19dfe6",
    "member_id": "8989447062e04a818baf9e073fd04fa7",
    "schema": "/v2/schemas/member",
    "status": "accepted",
    "updated_at": "2013-09-20T20:15:31Z"
}
```

</details>

***

#### 멤버 삭제

지정한 이미지의 멤버를 삭제합니다. 공유를 취소할 때 사용합니다. 반드시 지정한 이미지의 소속된 테넌트의 토큰으로 요청해야 합니다.

```
DELETE /v2/images/{imageId}/members/{memberId}
X-Auth-Token: {tokenId}
```

**요청**

이 API는 요청 본문을 요구하지 않습니다.

| 이름       | 종류     | 형식     | 필수 | 설명     |
| -------- | ------ | ------ | -- | ------ |
| imageId  | URL    | UUID   | O  | 이미지 ID |
| memberId | URL    | String | O  | 멤버 ID  |
| tokenId  | Header | String | O  | 토큰 ID  |

**응답**

이 API는 응답 본문을 반환하지 않습니다.
