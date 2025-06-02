
# 🔧 xnu-qemu-arm64-tools란?

**이 저장소는 QEMU 상에서 iOS 커널을 부팅하거나 디버깅하기 위해 사용되는 도구 모음**입니다.  
주로 iOS의 XNU 커널을 에뮬레이터 환경에서 실행하고 분석하려는 목적으로 사용됩니다.

---

## 📁 구성 디렉터리 및 설명

### 1. `bootstrap_scripts`
- **설명:** iOS 커널을 QEMU에서 부팅하기 위해 필요한 파일들을 **추출, 디코딩, 압축 해제**하는 Python 스크립트 모음입니다.
- **기능:**
  - iOS IPSW 파일 또는 시스템 이미지에서 필요한 부트 파일을 뽑아냄
  - 커널, 디바이스 트리, 캐시 파일 등을 가공

---

### 2. `gdb`
- **설명:** QEMU 위에서 실행 중인 iOS 커널을 **GDB를 통해 실시간 분석**할 수 있도록 도와주는 **GDB-Python 스크립트**
- **기능:**
  - 커널 쓰레드, task, 프로세스 정보 출력
  - 런타임 상태 확인

---

### 3. `ghidra`
- **설명:** **Ghidra 리버싱 툴**에서 사용하기 위한 스크립트 모음
- **기능:**
  - 자동 함수 정의
  - iOS 커널의 구조체 자동 적용
  - 분석 단축 기능 제공

---

### 4. `pic-binary`
- **설명:** **PIC (Position Independent Code)** 형식의 예제 바이너리로, 커널 메모리에 로드하여 실행 가능
- **사용 목적:**
  - 커널 코드 인젝션 테스트
  - 메모리 내 실행 실험

---

### 5. `aleph_bdev_drv`
- **설명:** Aleph Security에서 만든 **커스텀 블록 디바이스 드라이버**
- **역할:**
  - QEMU로 에뮬레이트된 iOS 시스템에 두 개의 블록 디바이스를 마운트
  - 커널 I/O 테스트 가능

---

### 6. `tcp-tunnel`
- **설명:** QEMU로 실행된 iOS 시스템과 외부 호스트 간 **TCP 연결을 터널링**하는 도구
- **기능:**
  - 내부 iOS ↔ 외부 호스트 간 통신
  - 다양한 네트워크 프로토콜 실험 가능

---

### 7. `xnu-kvm-lkm`
- **설명:** QEMU에서 KVM 가속 기능을 활용할 수 있도록 도와주는 리눅스 커널 모듈
- **특징:**
  - IDSR 미지원 커널에서도 KVM 가속 가능
  - 성능 개선

---

## ✅ 요약

| 구성 요소           | 주요 역할                                      |
|--------------------|-----------------------------------------------|
| `bootstrap_scripts`| iOS 커널 부트 파일 추출 및 전처리               |
| `gdb`              | QEMU 상에서 iOS 커널 런타임 분석               |
| `ghidra`           | iOS 커널 리버싱을 위한 Ghidra 스크립트         |
| `pic-binary`       | 커널 메모리 실행용 샘플 바이너리               |
| `aleph_bdev_drv`   | 가상 디바이스 마운트용 커스텀 드라이버         |
| `tcp-tunnel`       | iOS-QEMU ↔ 호스트 간 TCP 통신 터널링           |
| `xnu-kvm-lkm`      | IDSR 없이도 KVM 가속을 가능하게 해주는 모듈    |





# xnu-qemu-arm64-tools


*This repository includes the tools we use to boot/debug iOS kernel above QEMU.*

## bootstrap_scripts ##
Python scripts used for extract, decode, decompress the needed files to load the iOS kernel on QEMU.

## gdb ##
GDB-Python scripts that enable analysis of the kernel in run time (print threads, tasks, etc)

## ghidra ##
Ghidra scripts that we wrote to ease the reverse engineering process.

## pic-binary ##
A sample PIC (position-independent code) binary, that can be loaded into kernel memory for execution.

## aleph_bdev_drv ##
Custom Block Device Driver that is used to mount two block devices into iOS.

## tcp-tunnel ##
Used for tunneling TCP connections into and out of an iOS system emulated on QEMU.

## xnu-kvm-lkm ##
Linux kernel module that can be used to run QEMU with KVM, without using a custom kernel with IDSR exits support.
