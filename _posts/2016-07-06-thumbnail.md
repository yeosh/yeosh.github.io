---
layout: post
title: GDI+ - thumbnail
published: true
---

GDI+로 thumbnail 그리기

```cpp
// GDI+를 사용하기 위한 헤더
#include <Gdiplus.h>
#pragma comment(lib, "Gdiplus.lib")
using namespace Gdiplus;

Image image(filename);
Graphics graphics(hdc);
UINT width = 400, height = 400;
int xpos = 10, ypos = 10;

Image* thumb = image.GetThumbnailImage(width, height, NULL, NULL);
graphics.DrawImage(thumb, xpos, ypos, width, height);

delete thumb;
```

## Reference
[GetThumbnailImage](https://msdn.microsoft.com/ko-kr/library/windows/desktop/ms535394(v=vs.85).aspx)
