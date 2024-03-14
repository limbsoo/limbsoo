# Profile
___

이름: 권혁수

생년월일 : 1995-09-09

이메일 : rnjs909@naver.com

블로그 : [https://limbsoo.github.io](https://limbsoo.github.io/)

#  Skills
___
**Langauages**
- C++ 
- C# 
- HLSL

**Frameworks**
- Directx11
- Unity
- OpenGL

**Tools**
- Visual Studio

#  Do
___

## 블록 배치 기반 난이도 측정에 따른 Match-3 게임 맵 자동 생성 (2023.03 - 2023.12)

개발 도구 : Unity(2021.3.27f1), Vusual studio 2022
개발 언어 : C#, Python
사용 에셋 : MK - Forest Match 3 Game Asset

Match-3 게임의 모든 맵을 사람이 직접 만들고 난이도를 판별하는 것은 힘들다. 따라서 블록 배치 정도에 따라 난이도를 판별, 원하는 난이도의 맵을 유전 알고리즘을 통한 세대를 반복하여 자동으로 생성하는 알고리즘을 구현했다.


기능
- 실제 플레이 불가능한 맵 발생 방지
- FI-2Pop 알고리즘을 통한 적합도의 분산 감소 및 최적해 탐색 세대 감소
- 목표 우선 제거 자동 플레이
- 오브젝트 풀을 통한 자동 플레이 시간 감소
- 회귀 분석을 통한 특수 블록 별 스왑 횟수 증가량 측정




## 효율적인 모션 블러 효과 구현 (2022.01 - 2023.02)

개발 도구 : DirectX 11, Vusual studio 2019
개발 언어 : C++, HLSL

기존 accumulation 방식은 실제로 모션 블러가 발생하는 방식을 따라 구현한 모션 블러 생성 알고리즘이나, 높은 품질의 모션 블러를 구현할수록 필요 이미지의 개수가 급격히 증가하여 성능에 영향을 준다. 따라서 이를 효율적으로 구현하는 알고리즘을 고안하였다.

구현
1. accumulation 방식을 통한 모션 블러 효과 구현 (2022.01 - 2022.02)
2. 모션 벡터 공유를 통한 모션 블러 효과 구현 (2022.02 - 2022.03)
3. 다층 모션 벡터 활용 모션 블러 효과 구현 (2022.04 - 2022.08)
4. Stencil routing을 통한 다층 모션 벡터 활용 모션 블러 효과 구현 (2022.08 - 2023.01)


기능
- HLSL의 Discard()를 활용한 depth peeling layer image rendering
- stencil routing을 활용, stencil buffer를 통해 depth peeling layer image rendering
- Pack, Unpack을 통해 motion blur에 활용하는 rendering image 수 감소
- intersect 검사 알고리즘을 통해 현재 픽셀을 지나는 motion vector 탐색
- 픽셀 별 sampling 횟수에 따른 신뢰 정도를 측정, 이를 통한 디노이징



## DirectX 11 환경 렌더링 (2021.10 - 2021.12)

개발 도구 : DirectX 11, Vusual studio 2019
개발 언어 : C++, HLSL

DXUT 라이브러리를 활용, DirectX11 framework와 rendering pipeline을 구현하고 Lighting, Shadow mapping, Environment Mapping 등 다양한 기법들을 구현하였다.



## OpenGL 환경 렌더링 (2021.07 - 2021.10)

개발 도구 : OpenGL, Vusual studio 2019
개발 언어 : C++

스캔라인 기법을 통해 Texture mapping, Shadow mapping, Environment Mapping 등 다양한 기법들을 수식 계산을 통해 구현하고, glut 라이브러리를 활용 렌더링 이미지를 구현하였다.
