# 익상이가 만든 운동 분석 프로그램 설정 가이드

## 1. 필요한 라이브러리 설치

코드를 실행하려면 다음의 Python 라이브러리가 필요합니다:

- **Python 3.x** (3.7 이상 권장)
- **OpenCV** (`cv2`)
- **NumPy** (`numpy`)
- **MediaPipe** (`mediapipe`)
- **Pillow** (`PIL`)
- **datetime** (내장 모듈)
- **math** (내장 모듈)
- **json** (내장 모듈)

### 설치 방법:

터미널(또는 명령 프롬프트)을 열고 다음 명령어를 입력하여 필요한 라이브러리를 설치하세요:

```bash
pip install opencv-python numpy mediapipe Pillow
```

**참고:** `pip` 대신 `pip3`를 사용해야 할 수도 있습니다.

## 2. 웹캠 연결 및 설정

코드는 웹캠을 통해 실시간 영상을 받아와 처리합니다. 따라서 컴퓨터에 웹캠이 연결되어 있어야 하며, 웹캠이 정상적으로 작동하는지 확인하세요.

## 3. 한글 폰트 설정

코드에서 한글 텍스트를 이미지에 출력하기 위해 한글 폰트가 필요합니다. 코드에서는 다음과 같이 폰트를 지정하고 있습니다:

```python
font = ImageFont.truetype("/System/Library/Fonts/AppleSDGothicNeo.ttc", font_size)
```

이 경로는 **macOS**의 시스템 폰트 경로입니다. 사용하는 운영 체제에 따라 폰트 파일의 경로를 변경해야 합니다.

### 운영 체제별 폰트 설정:

#### Windows:

1. **한글 폰트 확인:**
   Windows에서는 보통 `Malgun Gothic`(맑은 고딕) 폰트가 기본 설치되어 있습니다.

2. **폰트 경로 지정:**

   ```python
   font = ImageFont.truetype("C:/Windows/Fonts/malgun.ttf", font_size)
   ```

   또는 `malgun.ttf` 파일을 코드와 같은 디렉토리에 복사하고 다음과 같이 지정할 수 있습니다:

   ```python
   font = ImageFont.truetype("malgun.ttf", font_size)
   ```

#### macOS:

macOS에서는 이미 코드에 지정된 경로를 사용할 수 있습니다. 다른 폰트를 사용하려면 `/Library/Fonts` 또는 `~/Library/Fonts` 디렉토리에서 원하는 폰트 파일의 경로를 찾아 지정하세요.

#### Linux:

1. **한글 폰트 설치:**

   ```bash
   sudo apt-get install fonts-nanum
   ```

2. **폰트 경로 지정:**

   ```python
   font = ImageFont.truetype("/usr/share/fonts/truetype/nanum/NanumGothic.ttf", font_size)
   ```

### 주의 사항:

- 폰트 파일의 경로가 정확하지 않으면 코드 실행 시 에러가 발생합니다.
- 한글이 제대로 출력되지 않으면 폰트 파일이 한글을 지원하는지 확인하세요.
- 폰트 파일을 프로젝트 디렉토리에 복사한 후 경로를 지정하면 경로 문제를 줄일 수 있습니다.

## 4. 카메라 권한 설정

일부 운영 체제에서는 애플리케이션이 카메라에 접근하려면 권한이 필요합니다. 사용하는 IDE나 터미널이 카메라 접근 권한을 갖고 있는지 확인하세요.

- **Windows:** 보안 설정에서 해당 프로그램의 카메라 접근 권한을 허용하세요.
- **macOS:** 시스템 환경설정 > 보안 및 개인 정보 보호 > 개인 정보 보호 > 카메라에서 터미널 또는 IDE의 권한을 허용하세요.
- **Linux:** 일반적으로 추가 권한이 필요하지 않지만, 필요한 경우 웹캠 설정을 확인하세요.

## 5. MediaPipe 모델 다운로드

`MediaPipe`는 처음 사용 시 필요한 모델 파일을 자동으로 다운로드합니다. 네트워크 연결이 되어 있어야 하며, 방화벽이나 프록시 설정으로 인해 다운로드가 차단되지 않도록 확인하세요.

## 6. 코드 실행

모든 준비가 완료되면 코드를 실행할 수 있습니다.

1. **코드 저장:**
   제공된 코드를 예를 들어 `exercise_analysis.py`라는 이름의 파일로 저장합니다.

2. **코드 실행:**
   터미널에서 해당 파일이 있는 디렉토리로 이동한 후 다음 명령어를 실행합니다:

   ```bash
   python exercise_analysis.py
   ```

   또는 IDE(예: PyCharm, VSCode)를 사용하여 실행할 수 있습니다.

## 7. 운동 선택 및 목표 설정

코드를 실행하면 터미널에 다음과 같이 표시됩니다:

```
운동을 선택하세요:
1. 스쿼트
2. 푸시업
3. 풀업
선택 (1/2/3):
```

- 원하는 운동 번호를 입력하세요.
- 그 후, 목표 세트 수와 세트당 반복 횟수를 입력합니다.


## 8. 추가 고려 사항

### OpenCV 버전 확인

최신 버전의 OpenCV를 사용하는 것이 좋습니다. 일부 기능은 버전에 따라 동작이 다를 수 있습니다.

### MediaPipe 호환성

MediaPipe와 OpenCV의 버전 호환성이 중요합니다. 라이브러리 간 호환성 문제로 에러가 발생하면 다음 버전을 시도해 보세요:

- OpenCV: `opencv-python==4.5.3.56`
- MediaPipe: `mediapipe==0.8.7`

```bash
pip install opencv-python==4.5.3.56 mediapipe==0.8.7
```

### Python 버전

Python 3.7 이상을 사용하는 것이 권장됩니다.

## 9. 에러 발생 시 해결 방법

- **ImportError:** 모듈이 없다는 에러가 발생하면 해당 모듈을 설치했는지 확인하세요.
- **Font 관련 에러:** 폰트 파일 경로가 정확한지, 폰트 파일이 존재하는지 확인하세요.
- **Webcam 에러:** 웹캠이 다른 프로그램에서 사용 중인지, 또는 연결이 제대로 되어 있는지 확인하세요.
- **PermissionError:** 카메라 또는 파일 접근 권한이 없는 경우 권한 설정을 확인하세요.
- **AttributeError:** MediaPipe의 결과를 처리하는 부분에서 에러가 발생하면, MediaPipe 버전을 확인하고 최신 버전을 사용하세요.

## 10. 환경 설정 예시

### Windows에서의 예시

1. **필요한 라이브러리 설치:**

    ```bash
    pip install opencv-python numpy mediapipe Pillow
    ```

2. **폰트 파일 설정:**
   - `C:\Windows\Fonts\malgun.ttf` 경로를 사용하거나
   - `malgun.ttf` 파일을 코드와 같은 디렉토리에 복사 후 `font = ImageFont.truetype("malgun.ttf", font_size)`로 설정

3. **코드 실행:**

    ```bash
    python exercise_analysis.py
    ```

### macOS에서의 예시

1. **필요한 라이브러리 설치:**

    ```bash
    pip install opencv-python numpy mediapipe Pillow
    ```

2. **폰트 파일 설정:**
   - 기본 설정된 `/System/Library/Fonts/AppleSDGothicNeo.ttc`를 그대로 사용

3. **코드 실행:**

    ```bash
    python exercise_analysis.py
    ```

### Linux(Ubuntu)에서의 예시

1. **한글 폰트 설치:**

    ```bash
    sudo apt-get install fonts-nanum
    ```

2. **필요한 라이브러리 설치:**

    ```bash
    pip install opencv-python numpy mediapipe Pillow
    ```

3. **폰트 파일 설정:**

    ```python
    font = ImageFont.truetype("/usr/share/fonts/truetype/nanum/NanumGothic.ttf", font_size)
    ```

4. **코드 실행:**

    ```bash
    python exercise_analysis.py
    ```

## 11. 추가 팁

- **IDE 사용 추천:** Visual Studio Code, PyCharm 등의 IDE를 사용하면 디버깅과 코드 실행이 편리합니다.
- **가상 환경 사용:** `venv` 또는 `conda`를 사용하여 가상 환경을 만들어 라이브러리 버전 관리를 쉽게 할 수 있습니다.
- **라이브러리 버전 확인:** `pip list` 명령어를 사용하여 설치된 라이브러리의 버전을 확인하세요.

