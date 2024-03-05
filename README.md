이름: 권혁수

생년월일 : 1995-09-09

이메일 : rnjs909@naver.com

블로그 : [https://limbsoo.github.io/](https://limbsoo.github.io/)

#  Skills
___
Langauages
- C
- C++ 
- C# 
- HLSL

Frameworks
- Directx11
- Unity
- OpenGL

Tools
- Visual Studio

#  Do
___

2021.07 - 21.10 [Blog](https://limbsoo.github.io/tags/opengl/), [Github](https://github.com/limbsoo/openGL)
- openGL glut 라이브러리를 활용, 스캔 라인을 통한 렌더링 효과를 구현하였습니다.
	(Texture mapping, Shadow mapping, Environment Mapping 등)
	
	
 
2021.10 - 21.12  	[Blog](https://limbsoo.github.io/tags/tutorial/),  [Github](https://github.com/limbsoo/DirectX11)
- DirectX11 환경에서 DX11 rendering pipeline을 통한 렌더링 효과를 구현하였습니다.
	(Lighting, Shadow mapping, Environment Mapping 등)
	


2022.01 - 2023.02  [Blog](https://limbsoo.github.io/tags/motionblur/),  [Github](https://github.com/limbsoo/DirectX11)

2022.01 - 2022.02 	[Blog](https://limbsoo.github.io/posts/DX11-Motion-Blur-using-Accumulation-method/),  [Github](https://github.com/limbsoo/DirectX11/tree/master/accumulation_motionblur)
- accumulation 방식을 통한 모션 블러 효과 구현  
	모션 블러 생성을 위해 한 프레임에서 발생한 물체의 움직임을 일정 횟수만큼 나누고, 이를 하나의 이미지로 합쳐 모션 블러 효과를 생성하는 방법을 구현하였습니다.
	
![image](https://github.com/limbsoo/limbsoo.github.io/assets/96706760/2779e5c6-68e9-4653-8f07-138d8c489447)



- motion vector sharing 방식을 통한 모션 블러 효과 구현  
	accumulation 방식을 통한 모션 블러 효과 생성 시, 효과 생성에 필요한 이미지의 개수가 늘어남에 따라 급격한 성능 저하를 보이므로, 모션 벡터를 통해 이동하는 물체의 다음 픽셀을 예측, 샘플하여 모션 블러 효과를 구현하였습니다.
	
	[Blog](https://limbsoo.github.io/posts/DX11-Motion-Blur-using-motion-vector-sharing/),  [Github](https://github.com/limbsoo/DirectX11/tree/master/sharing_motionvector_motionblur)

![image](https://github.com/limbsoo/limbsoo.github.io/assets/96706760/a4f9d8bf-b388-4573-8c8b-f881ba85614d)



- depth 별 layer를 사용하는 motion vector sharing 모션 블러 효과 구현 
	기존 motion vector sharing 방식의 문제는 서로 다른 움직임을 가진 여러 물체 간 모션 블러 효과 범위가 중복 시, 일부 물체의 모션 블러 효과가 사라지는 현상이 발생하였습니다. 이는 샘플 위치에 이미 다른 물체가 존재 시, 해당 위치의 배경 정보를 가져오지 못해 발생하는 것으로, 이를 depth별 layer 이미지를 통해 해결하고 모션 블러 효과를 구현하였습니다.
	
	[Blog](https://limbsoo.github.io/posts/DX11-Motion-Blur-using-depth-peeling-layer/),  [Github](https://github.com/limbsoo/DirectX11/tree/master/depthpeeling_motionblur)


![image](https://github.com/limbsoo/limbsoo.github.io/assets/96706760/c5fdec6d-9feb-4836-9ee1-56589aedac33)



- stencil routing을 통한 depth 별 layer motion vector sharing 모션 블러 효과 구현
	기존 motion vector sharing에서 발생한 문제로, depth 별 layer motion vector sharing은 추가적인 이미지를 사용해야 하므로 성능 저하가 발생합니다. 이를 해결하기 위해stecil routing을 통한 렌더링을 진행, 기존 방법보다 더 좋은 성능으로 모션 블러 이미지를 생성하였습니다.
	
	[Blog](https://limbsoo.github.io/posts/DX11-Motion-Blur-stencil-routing/),  [Github](https://github.com/limbsoo/DirectX11/tree/master/depthpeeling_motionblur)

※ Stencil Routed Rendering
- Turn off Depth Test & Set multiple render target(renderTarget은 각각의 Stencil buffer와 연결)
- Stencil buffer를 (StencilRef ~ StencilRef + renderTarget - 1)로 초기화
- polygon이 픽셀을 cover할 때 마다 stencilRef와 똑같은 stencil 값을 가지는 renderTarget에만 색상을 저장하고 모든 renderTarget의 stencil값 1 감소
- 여러 개의 polygon이 동일한 픽셀을 cover하면 renderTarget 만큼 polygon의 색상이 renderTarget에 저장된다.


2023.03 - 2023.12 
- unity 환경에서 유전 알고리즘을 통한 Match-3 game map 자동 생성
	match-3 게임의 모든 맵을 사람이 직접 만들고, 난이도를 테스트하는 것은 어려우므로,맵의 난이도를 블록 배치 정도에 따라 나누고, 유전 알고리즘을 사용하여 원하는 난이도의 맵을 자동으로 생성하는 알고리즘을 구현하였습니다.
	
	[Blog](https://limbsoo.github.io/tags/match-3game/),  [Github](https://github.com/limbsoo/3match_genetic-algorithm_unity)

![image](https://github.com/limbsoo/limbsoo.github.io/assets/96706760/52a442cf-e268-40d1-85e6-5fc2202caf3f)

