
이름: 권혁수

생년월일 : 1995-09-09

이메일 : rnjs909@naver.com

[Blog](https://limbsoo.github.io/)

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

2021.07 - 21.10 
- openGL glut 라이브러리를 활용, 스캔 라인을 통한 렌더링 효과를 구현하였습니다.
	(Texture mapping, Shadow mapping, Environment Mapping 등)
	
	[Blog](https://limbsoo.github.io/tags/opengl/), [Github](https://github.com/limbsoo/openGL)
 
2021.10 - 21.12  
- DirectX11 환경에서 DX11 rendering pipeline을 통한 렌더링 효과를 구현하였습니다.
	(Lighting, Shadow mapping, Environment Mapping 등)
	
	[Blog](https://limbsoo.github.io/tags/tutorial/),  [Github](https://github.com/limbsoo/DirectX11)

2022.01 - 2023.02  [Blog](https://limbsoo.github.io/tags/motionblur/),  [Github](https://github.com/limbsoo/DirectX11)
- accumulation 방식을 통한 모션 블러 효과 구현  
	모션 블러 생성을 위해 한 프레임에서 발생한 물체의 움직임을 일정 횟수만큼 나누고, 이를 하나의 이미지로 합쳐 모션 블러 효과를 생성하는 방법을 구현하였습니다.
	
	[Blog](https://limbsoo.github.io/posts/DX11-Motion-Blur-using-Accumulation-method/),  [Github](https://github.com/limbsoo/DirectX11/tree/master/accumulation_motionblur)

	한 프레임에서 발생한 물체의 움직임을,
<p align="center"><img src="https://github.com/limbsoo/limbsoo.github.io/assets/96706760/544d21f9-6471-47f8-9c2e-15a5e6e6a990" width="300px"></p>


이미지를 겹쳐, 픽셀 색상 결정
<p align="center"><img src="https://github.com/limbsoo/limbsoo.github.io/assets/96706760/e33c9c9b-cfe8-4736-8609-81277e088aef" width="700px"></p>



- motion vector sharing 방식을 통한 모션 블러 효과 구현  
	accumulation 방식을 통한 모션 블러 효과 생성 시, 효과 생성에 필요한 이미지의 개수가 늘어남에 따라 급격한 성능 저하를 보이므로, 모션 벡터를 통해 이동하는 물체의 다음 픽셀을 예측, 샘플하여 모션 블러 효과를 구현하였습니다.
	
	[Blog](https://limbsoo.github.io/posts/DX11-Motion-Blur-using-motion-vector-sharing/),  [Github](https://github.com/limbsoo/DirectX11/tree/master/sharing_motionvector_motionblur)
<center><img src="https://github.com/limbsoo/limbsoo.github.io/assets/96706760/0685941d-3ecc-4347-b7a2-bd0f5d85d5ea" alt width=600>
<em>물체의 이동 정보를 가진 모션 벡터</em>
</center>


<center><img src="https://github.com/limbsoo/limbsoo.github.io/assets/96706760/756624ed-7559-4c5b-ad85-c580d955d539" alt width="100%">
<em></em>
</center>

<center><img src="https://github.com/limbsoo/limbsoo.github.io/assets/96706760/0bfc1145-1b84-4687-a778-0e645785c3e6" alt width="100%">
<em>픽셀 위치의 모션 벡터를 통해 샘플 위치 결정</em>
</center>



- depth 별 layer를 사용하는 motion vector sharing 모션 블러 효과 구현 
	기존 motion vector sharing 방식의 문제는 서로 다른 움직임을 가진 여러 물체 간 모션 블러 효과 범위가 중복 시, 일부 물체의 모션 블러 효과가 사라지는 현상이 발생하였습니다. 이는 샘플 위치에 이미 다른 물체가 존재 시, 해당 위치의 배경 정보를 가져오지 못해 발생하는 것으로, 이를 depth별 layer 이미지를 통해 해결하고 모션 블러 효과를 구현하였습니다.
	
	[Blog](https://limbsoo.github.io/posts/DX11-Motion-Blur-using-depth-peeling-layer/),  [Github](https://github.com/limbsoo/DirectX11/tree/master/depthpeeling_motionblur)

<center><img src="https://github.com/limbsoo/limbsoo.github.io/assets/96706760/8a1325dc-22fa-4a32-8fa9-72da38d97182" alt width=700>
<em>기존 motion vector sharing 방식에서 일부 물체의 모션 블러 효과가 사라지는 현상이 발생</em>
</center>



<center><img src="https://github.com/limbsoo/limbsoo.github.io/assets/96706760/ac53a233-08b0-485f-b327-d9b06a6cd140" alt width=700>
<em>depth별 layer 이미지를 통해 가려진 배경 색상을 샘플</em>
</center>


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


<center><img src="https://github.com/limbsoo/limbsoo.github.io/assets/96706760/8362c2ac-eef4-44a9-ac38-bb5411e04fda" alt width=500>
<em></em>
</center>



<center><img src="https://github.com/limbsoo/limbsoo.github.io/assets/96706760/a2940bb8-8e11-4502-a736-a78f8adc4d73" alt width=600>
<em>블록 위치에 따라 발생할 수 있는 매치 발생 경우의 수 측정</em>
</center>


<center><img src="https://github.com/limbsoo/limbsoo.github.io/assets/96706760/37d24283-c701-4db5-8845-3d253a539b90" alt width=600>
<em>특수 블록 배치 시, 경우의 수 감소 정도에 따른 난이도 측정</em>
</center>



<center><img src="https://github.com/limbsoo/limbsoo.github.io/assets/96706760/2d0a3c4f-c792-431e-b801-0ad17a92de4c" alt width=500>
<em></em>
</center>

