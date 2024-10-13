# SWE_2021_41_2024_2_week_6

## Week 4 - Google Colab 학습

1. **Google Colab**
  - Jupyternotebook development environment based on Cloud server4
  - Accessibility, Resources, Collaboration
  
2. **Assignment**
  - **Happy Number**
  Write an algorithm to determine if a number **n** is happy.
  - 풀이 코드 
  ```python
  def isHappy(n):
  exist = set()
  while n != 1 and n not in exist:
    exist.add(n)
    n = sum([int(i)**2 for i in str(n)])
    return n == 1

  print(isHappy(19))
  print(isHappy(2))
  ```
  - 풀이 과정 :
  숫자의 각 자릿수 제곱의 합이 1이 되면 True를 반환하도록 작성
  이미 처리한 숫자는 집합에 저장해 중복을 방지하고, 무한 루프가 발생하면 False를 반환.
---

## Week 5 - Docker 학습

1. **Docker**
   - Docker는 애플리케이션을 컨테이너에 패키징하여 개발 환경과 배포 환경 간의 일관성을 유지하도록 하는 도구
   - 컨테이너는 **경량 가상화 환경**으로, 애플리케이션과 필요한 의존성을 함께 묶어 어디서나 동일한 환경에서 실행할 수 있게 해줌

2. **Assignment**
   - **Ubuntu 기반 Docker 컨테이너를 생성하고** Git과 Python3를 설치한 환경을 구성하는 것
   - Host Directory, Container 간의 **바인드 마운트**를 설정해 파일을 공유

3. **과제 진행**
   - Ubuntu 이미지를 기반으로 컨테이너를 생성
     ```bash
     docker run -it --name ossp-container -v /Users/daram/Desktop:/mnt/desktop ubuntu
     ```
   - 컨테이너 내부에서 Git과 Python3를 설치
     ```bash
     apt-get update
     apt-get install -y git python3
     ```
   - 설치된 버전을 확인
     ```bash
     git --version
     python3 --version
     ```

4. **바인드 마운트 확인**
   - 바인드 마운트가 제대로 설정되었는지 확인
     ```bash
     docker inspect --format="{{ .HostConfig.Binds }}" ossp-container
     ```
5. **과제 실행 결과**
   ```bash
    docker exec ossp-container cat /etc/os-release
   ```
   ```
    PRETTY_NAME="Ubuntu 24.04.1 LTS"
    NAME="Ubuntu"
    VERSION_ID="24.04"
    VERSION="24.04.1 LTS (Noble Numbat)"
    VERSION_CODENAME=noble
    ID=ubuntu
    ID_LIKE=debian
    HOME_URL="https://www.ubuntu.com/"
    SUPPORT_URL="https://help.ubuntu.com/"
    BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
    PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
    UBUNTU_CODENAME=noble
    LOGO=ubuntu-logo
   ```
    
    ```
    docker exec ossp-container git --version
    ```
    ```
    git version 2.43.0
    ```
    ```
    docker exec ossp-container python3 --version
    ```
    ```
    Python 3.12.3
    ```
    ```
    docker inspect --format="{{ .HostConfig.Binds }}" ossp-container
    ```
    ```
    [/Users/daram/Desktop:/mnt/desktop]
    ```
