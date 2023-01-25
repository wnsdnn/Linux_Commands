# Linux_Commands
### 내가 쓸려고 만든 리눅스 명령어 모음집 

우분투 설치 [참고](https://cpuu.postype.com/post/10265353)

<br>

1. 디렉토리 생성하기

    ```
    mkdir [옵셥] [디렉토리명]
    ```

    #### 자주 사용하는 옵션

    ```
    -m: 디렉토리 생성 시 권한 설정
    -p: 하위 디렉토리까지 함께 생성
    -v: 디렉토리를 생성하고 생성된 디렉토리에 대한 메시지를 출력
    ```

    #### 예시
    ```
    wnsdn@DESKTOP-7NKLFP4:~$ mkdir -p tests/test1
    mkdir -p [디렉토리명]/[디렉토리명]/...

    wnsdn@DESKTOP-7NKLFP4:~$ mkdir -m 700 test1
    mkdir -m [권한] [디렉토리명]

    wnsdn@DESKTOP-7NKLFP4:~$ mkdir -v test2
    mkdir: created directory 'test2'
    mkdir -v [디렉토리명]
    ```

    #### 동시에 여러개 생성 가능
    ```
    mkdir test1 test2 test3
    ```
<br>
<br>

2. 디렉토리 이동하기 

    ```
    cd 디렉토리명
    ```
    ```
    cd .. : 상위 디렉토리로 이동
    cd . : 현재 위치한 폴더로 이동. 사실상 기능은 새로고침과 동일
    cd - : 이전에 위치했던 폴더로 이동. 윈도우의 뒤로 가기와 동일
    cd / : ROOT 디렉토리로 이동
    cd ~ : 홈 디렉토리로 이동
    ```
<br>

3. 디렉토리 삭제하기

    ```
    rmdir 디렉토리명 : 빈 디렉토리 삭제

    비어있지 않으면 다음 오류 발생
    // rmdir: failed to remove '디렉토리명': Directory not empty
    ```

    #### rm 옵션 사용 
    ```
    rm : 파일 및 디렉토리를 삭제 가능

    rm -d(--dir) : 빈 디렉토리 삭제
    rm -r(--recursive 또는 -R) : 비어 있지 않은 디렉토리 삭제
    ```


<br>

4. 디렉토리 파일 확인하기

    ```
    ls
    ```

    ```
    ls -a : 숨김파일을 포함하여 모든 파일의 목록을 출력
    ls -d : 현재 디렉토리의 정보를 출력
    ls -l : 파일의 상세정보를 출력
    ls -i : 첫번째 행의 inode 번호를 출력
    ls -A : (.)와 (..)를 제외한 모든 파일을 출력
    ls -F : 파일의 종류를 표시
    ls -L : 심벌릭 링크 파일의 경우 원본 파일의 정보를 출력
    ls -R : 하위 디렉토리의 목록까지 모두 출력
    ```

    #### 숨김파일 및 상세정보 출력
    ```
    wnsdn@DESKTOP-7NKLFP4:~$ ls
    a   abc
    wnsdn@DESKTOP-7NKLFP4:~$ ls -al
    -rw------- 1 wnsdn wnsdn   185 Jan 25 15:11 .bash_history
    -rw-r--r-- 1 wnsdn wnsdn   220 Jan 25 13:48 .bash_logout
    -rw-r--r-- 1 wnsdn wnsdn  3771 Jan 25 13:48 .bashrc
    drwxr-xr-x 3 wnsdn wnsdn  4096 Jan 25 14:39 a
    drwxr-xr-x 2 wnsdn wnsdn  4096 Jan 25 14:39 abc
    ```
    
<br>

5. 파일 생성하기

    ```
    touch [파일명] : 파일의 생성과 파일의 날짜, 시간을 변경
    cat > [파일명] : 파일 생성
    vi [파일명] : vi 편집기 실행
    ```

    #### vi 사용법

    #### 명령 모드(command mode)에서의 명령어들
    ```
    esc 클릭후 해당 명령 입력
    - 명령어 입력후 엔터 안쳐도 됨

    i : 현재 커서 위치에 삽입 (입력모드로 넘어감) 
    a : 현재 커서 바로 다음위치에 삽입 (입력모드로 넘어감)
    o : 현재 줄 다음 위치에 삽입 (입력모드로 넘어감)
    x : 커서가 위치한 곳의 글자 1개 삭제. (5x : 문자 5개 삭제) 
    dw : 커서가 위치한 곳에서 부터 단어 삭제 (커서가 위치한 곳 부터 띄어쓰기 까지)
    dd : 커서가 위치한 곳의 한 줄 삭제 (삭제이지만, p로 복구가능)
    u : 방금 한 명령 취소 (ctrl + z)
    yy : 현재 줄 복사 (5줄 복사 : 5yy)
    p : 현재 커서가 있는 줄 바로 아래에 내용 붙여넣기 (현재 커서 아래부터 ctrl + v)
    (N)dd : N행 잘라내기 (ctrl + x) / vi에서 여러줄을 삭제하고 싶을때도 (N)dd 를 사용하면 됩니다. (N에는 숫자가 들어갑니다)

    등등
    ```

    #### 마지막 행 모드(last line mode)에서의 명령어들
    ```
    esc 클릭후 (:) 누른뒤 해당 명령 입력
    - 명령어 입력후 엔터 쳐야함

    w : 현재 파일명으로 파일 저장. (저장만 함 꺼지지는 않음) 
    w [파일명] : 입력한 파일명으로 파일 저장. (저장만 함 꺼지지는 않음)
    q : vi 종료 (저장되지 않음)
    q! : vi 강제 종료 (!가 붙으면 강제로 수행)
    wq : 저장 후 종료 
    wq! : 강제 저장 후 종료 (!가 붙으면 강제로 수행) 

    등등
    ```

    [vi 명령어 참고](https://blockdmask.tistory.com/25)

<br>


6. 파일 확인하기

<br>


7. 파일 삭제하기

    rm -rf 파일명

<br>




