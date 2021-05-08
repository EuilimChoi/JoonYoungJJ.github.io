---
title:  "위키 4 - Pinvoke(P/Invoke) 함수에 대한 설명"
excerpt: "Pinvoke(P/Invoke) 함수에 대한 설명"
permalink: wiki/4
image: 
# Site Author
author:
  name             : "Joon"
  avatar           : "/assets/image/JoonProfile.png" # path of avatar image, e.g. "/assets/images/bio-photo.jpg"
  bio              : "#Developers #CSharp #VBA"
  location         : "Seoul, Korea"
  email            :
  links:
    - label: "GitHub"
      icon: "fab fa-fw fa-github"
      url: "https://github.com/JoonYoungJJ/JoonYoungJJ.github.io"
    # - label: "Instagram"
    #   icon: "fab fa-fw fa-instagram"
      # url: "https://instagram.com/"
      
categories:
  - wiki
tags:
  - pinvoke
 
date: 2021-05-08
last_modified_at: 2021-05-08
---

Pinvoke는 [CLI](https://en.wikipedia.org/wiki/Common_Language_Infrastructure)의 일종이다. CLI (Common Language Infrastructure) 는 Microsoft에 의해 제안된 것으로 *.exe, *.dll 등 고급 프로그래밍 언어로 개발된 SW를 플랫폼에 관계없이 사용할 수 있도록 하는 표준이다. Pinvoke는 Platform Invoke의 줄임말로 P/Invoke라는 식으로 흔히 불린다. P/Invoke란, 관리코드 (Managed Code)인 고급 프로그래밍언어 (C#, VBA, ...) 에서 비관리코드 (Unmanaged Code) 라이브러리를 사용할 수 있도록 해주는 기술을 말한다.  

- [[Wikipedia] PInvoke Service](https://en.wikipedia.org/wiki/Platform_Invocation_Services)  

관리코드에서 비관리코드 라이브러리를 사요할 때 또 중요하게 다루어지는 개념은 마샬링이다. 관리코드에서 사용하는 메모리와 비관리코드에서 사용하는 구조체는 그 형태가 다르기 때문에 비관리코드에서 사용하는 구조체를 관리코드의 구조체로 변경하는 작업이 마샬링이다.  
관리코드와 비관리코드의 구조체의 형태의 차이에 대해 자세히 알아보려 했지만, 원하는 글을 찾기가 어려웠다. 개인적인 생각으로는 관리코드에서는 비관리코드의 구조체의 [래퍼클래스](http://www.tcpschool.com/java/java_api_wrapper) 를 사용하는 정도일 것 같다.  

- [[Microsoft Docs] How to: Marshal Structures Using PInvoke](https://docs.microsoft.com/en-us/cpp/dotnet/how-to-marshal-structures-using-pinvoke?view=msvc-160)  

마샬링을 사용하는 방법은 어렵지 않았다. 비관리코드와 관리코드를 모두 지원하는 c++을 사용하여 비관리코드를 관리코드로 마샬링하는 아래의 예제 코드를 참조하면 이 내용에 대해 조금이라도 이해가 될 듯 하다.  

```c++
// TraditionalDll3.cpp
// compile with: /LD /EHsc
#include <iostream>
#include <stdio.h>
#include <math.h>

#define TRADITIONALDLL_EXPORTS
#ifdef TRADITIONALDLL_EXPORTS
   #define TRADITIONALDLL_API __declspec(dllexport)
#else
   #define TRADITIONALDLL_API __declspec(dllimport)
#endif

#pragma pack(push, 8)
struct Location {
   int x;
   int y;
};
#pragma pack(pop)

extern "C" {
   TRADITIONALDLL_API double GetDistance(Location, Location);
   TRADITIONALDLL_API void InitLocation(Location*);
}

double GetDistance(Location loc1, Location loc2) {
   printf_s("[unmanaged] loc1(%d,%d)", loc1.x, loc1.y);
   printf_s(" loc2(%d,%d)\n", loc2.x, loc2.y);

   double h = loc1.x - loc2.x;
   double v = loc1.y = loc2.y;
   double dist = sqrt( pow(h,2) + pow(v,2) );

   return dist;
}

void InitLocation(Location* lp) {
   printf_s("[unmanaged] Initializing location...\n");
   lp->x = 50;
   lp->y = 50;
}
```

```c++
// MarshalStruct_pi.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

[StructLayout(LayoutKind::Sequential, Pack=8)]
value struct MLocation {
   int x;
   int y;
};

value struct TraditionalDLL {
   [DllImport("TraditionalDLL3.dll")]
   static public double GetDistance(MLocation, MLocation);
   [DllImport("TraditionalDLL3.dll")]
   static public double InitLocation(MLocation*);
};

int main() {
   MLocation loc1;
   loc1.x = 0;
   loc1.y = 0;

   MLocation loc2;
   loc2.x = 100;
   loc2.y = 100;

   double dist = TraditionalDLL::GetDistance(loc1, loc2);
   Console::WriteLine("[managed] distance = {0}", dist);

   MLocation loc3;
   TraditionalDLL::InitLocation(&loc3);
   Console::WriteLine("[managed] x={0} y={1}", loc3.x, loc3.y);
}
``` 

위와 같이 번거로운 작업을 해야하는 이유가 없을 것 같지만, 윈도우 프로그램 개발시 간혹 Window API 등 비관리코드 기반 라이브러리에서의 특정 기능이 필요한 경우가 발생하면 어쩔 수 없이 위와 같이 코드를 작성해야 한다.  
과거에 엑셀 AddIn (VSTO)를 개발하며 C언어 기반의 Window API를 처음 접했고, 엑셀에 적용되어 있는 기술을 조금 변형하여 사용하기 위해 마샬링, PInvoke 를 공부해야만 했었다. 공부를 하면 할 수록 비효율적인 언어라고 생각이 들었지만, 그 당시에는 결국 어쩔 수 없이 사용할 수 밖에 없었다.  
그나마 이를 개선하여 C++ 클래스로 묶은 라이브러리인 MFC가 등장했지만 이 역시 원하는 GUI를 구성하거나, 특정 기능을 구현하기 위해서는 대부분의 프레임워크를 사용할 때보다 훨씬 더 많은 시간이 요구된다. MFC는 과거에 MFC를 통해 만들어진 프로그램을 유지보수하는 정도로만 이용된다고 하니 신기술이 적용이 요구되는 사업분야에서는 거의 사장되어가는 추세라고 생각하면 될 것 같다.  