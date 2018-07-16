# 세미풀 마이닝 가이드

https://zny.semi-pool.com/

BitZeny는 CPU 마이닝에 최적화된 `yescrypt`를 채용한 일본 최초의 CPU 코인이다. 2018년 이후 GPU 마이닝이 가능하게 되었지만 효율은 `1 : 0.9` 수준으로 CPU가 약 10% 가량 빠르며 전기세도 더 저렴하다.

자세한 사항은 다음을 참고:
https://www.alphawiki.org/w/%EB%B9%84%ED%8A%B8%EC%A0%9C%EB%8B%88

## CPU 마이닝
BitZeny의 CPU 마이너에는 총 4가지가 있다.

1. cpuminer-bitzeny-2.4-official
https://github.com/bitzeny/cpuminer
2. cpuminer-macchky-2.6
https://github.com/macchky/cpuminer
3. cpuminer-opt
https://github.com/JayDDee/cpuminer-opt
4. cpuminer-kawaii
https://github.com/cryptozeny/cpuminer-kawaii

현재 (2018-07-17) 기준 세미풀에서 추천하는 것은 `cpuminer-macchky-2.6`이다.
https://github.com/macchky/cpuminer

벤치마크는 다음을 참고:
https://github.com/cryptozeny/cpuminer-kawaii/wiki/bitzeny-cpuminer-benchmark

## CPUMINER 다운로드
v.2.6.0 버젼이 현재 (2018-07-17) 기준 최신버젼이다. `ZNYminer260.zip`를 다운받는다.
https://github.com/macchky/cpuminer/releases

## CPUMINER 실행
지갑주소는 각자의 개인주소로 바꾼다.

### Windows
저사양 디바이스: 라즈베리파이, 구형컴퓨터, 스마트폰
```bash
minerd260.exe -a yescrypt -o stratum+tcp://zny.semi-pool.com:3333 -u ZyWJL5qp3qZQW85HVoT3ba2feJYsZ7aQ2v
```
일반적인 PC: 라이젠, 인텔
```bash
minerd260.exe -a yescrypt -o stratum+tcp://zny.semi-pool.com:5555 -u ZyWJL5qp3qZQW85HVoT3ba2feJYsZ7aQ2v
```
고성능 클라우드: GPU 4way 이상 혹은 48코어 이상
```bash
minerd260.exe -a yescrypt -o stratum+tcp://zny.semi-pool.com:7777 -u ZyWJL5qp3qZQW85HVoT3ba2feJYsZ7aQ2v
```

### Linux
저사양 디바이스: 라즈베리파이, 구형컴퓨터, 스마트폰
```bash
./linux/minerd -a yescrypt -o stratum+tcp://zny.semi-pool.com:3333 -u ZyWJL5qp3qZQW85HVoT3ba2feJYsZ7aQ2v
```
일반적인 PC: 라이젠, 인텔
```bash
./linux/minerd -a yescrypt -o stratum+tcp://zny.semi-pool.com:5555 -u ZyWJL5qp3qZQW85HVoT3ba2feJYsZ7aQ2v
```
고성능 클라우드: GPU 4way 이상 혹은 48코어 이상
```bash
./linux/minerd -a yescrypt -o stratum+tcp://zny.semi-pool.com:7777 -u ZyWJL5qp3qZQW85HVoT3ba2feJYsZ7aQ2v
```

### MacOS
현재 (2018-07-17) 기준 맥용 바이너리가 공개되지 않았지만 직접 컴파일이 가능하다.
다음을 참고: https://medium.com/@cryptozeny/macos-%EC%97%90%EC%84%9C-bitzeny-%EC%B1%84%EA%B5%B4%ED%95%98%EA%B8%B0-ad4267e860aa

```bash
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

brew tap bitzenycoredevelopers/bitzeny

brew install cpuminer-macchky
```

저사양 디바이스: 라즈베리파이, 구형컴퓨터, 스마트폰
```bash
/usr/local/Cellar/cpuminer-macchky/2.6.0/bin/minerd -o stratum+tcp://zny.semi-pool.com:3333 -u ZyWJL5qp3qZQW85HVoT3ba2feJYsZ7aQ2v
```
일반적인 PC: 라이젠, 인텔
```bash
/usr/local/Cellar/cpuminer-macchky/2.6.0/bin/minerd -o stratum+tcp://zny.semi-pool.com:5555 -u ZyWJL5qp3qZQW85HVoT3ba2feJYsZ7aQ2v
```
고성능 클라우드: GPU 4way 이상 혹은 48코어 이상
```bash
/usr/local/Cellar/cpuminer-macchky/2.6.0/bin/minerd -o stratum+tcp://zny.semi-pool.com:7777 -u ZyWJL5qp3qZQW85HVoT3ba2feJYsZ7aQ2v
```

## GPU 마이닝
ccminer를 KlausT가 개조한 버젼에 BitZeny를 채굴하는 코드가 추가된 버젼이 공개되었다.

### GPUMINER(ccminer) 다운로드

`KlausT-8.21-mod-r6`를 다운받는다.
https://1drv.ms/u/s!Aud1FauQ46vHh1B5NYbLOB2bQlOt

`yescrypt`가 `yescryptr8`로 변경됨에 주의!

*NVIDIA gtx1080에서 작동을 확인하였으며, AMD는 테스트하지 못했다.*

### Windows
1way: gtx1060/70/80/Ti
```bash
ccminer.exe -a yescryptr8 -o stratum+tcp://zny.semi-pool.com:5555 -u ZyWJL5qp3qZQW85HVoT3ba2feJYsZ7aQ2v
```
3way 이상
```bash
ccminer.exe -a yescryptr8 -o stratum+tcp://zny.semi-pool.com:7777 -u ZyWJL5qp3qZQW85HVoT3ba2feJYsZ7aQ2v
```

### Linux
직접 컴파일을 해야하며 `nvidia-396` 및 `cuda-9.2`가 필요하다.
```bash
# nvidia-396 \
sudo add-apt-repository ppa:graphics-drivers/ppa && \
sudo apt-get update && \
sudo apt-get install nvidia-396 && \
\
# cuda-9.2 \
cd && \
wget https://developer.nvidia.com/compute/cuda/9.2/Prod/local_installers/cuda_9.2.88_396.26_linux && \
wget https://developer.nvidia.com/compute/cuda/9.2/Prod/patches/1/cuda_9.2.88.1_linux && \
chmod +x cuda_9.2.88_396.26_linux && \
chmod +x cuda_9.2.88.1_linux && \
./cuda_9.2.88_396.26_linux --extract=$HOME && \
sudo ./cuda-linux.9.2.88-23920284.run
\
# Configure Runtime Library \
sudo bash -c "echo /usr/local/cuda/lib64/ > /etc/ld.so.conf.d/cuda.conf" && \
sudo ldconfig && \
sudo bash -c "echo /usr/local/cuda/bin > /etc/environments" && \
sudo ldconfig && \
\
# cuballoon install \
sudo apt-get install \
build-essential autoconf automake libssl-dev libcurl4-openssl-dev libjansson-dev zlib1g-dev screen git && \
cd && \
sudo apt-get install wget unzip && \
wget https://github.com/semipool/semi-pool.com/raw/master/ccminer-KlausT-8.21-mod-r6-src.zip && \
unzip ccminer-KlausT-8.21-mod-r6-src.zip -d ./ && \
cd ccminer-KlausT-8.21-mod-r6/ && \
./autogen.sh && \
./build.sh
```

1way: gtx1060/70/80/Ti
```bash
./ccminer -a yescryptr8 -o stratum+tcp://zny.semi-pool.com:5555 -u ZyWJL5qp3qZQW85HVoT3ba2feJYsZ7aQ2v
```
3way 이상
```bash
./ccminer -a yescryptr8 -o stratum+tcp://zny.semi-pool.com:7777 -u ZyWJL5qp3qZQW85HVoT3ba2feJYsZ7aQ2v
```

### MacOS
아직 시도해보지 않았다. 추후 추가예정

끝
