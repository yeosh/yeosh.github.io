---
layout: post
title: GDI+ - image orientation (EXIF)
published: true
---

GDI+에서 이미지의 orientation(회전율) 가져오기

```cpp
UINT total_buffer_size, num_properties;
image.GetPropertySize(&total_buffer_size, &num_properties);

PropertyItem* all_items = (PropertyItem*)malloc(total_buffer_size);
image.GetAllPropertyItems(total_buffer_size, num_properties, all_items);

for (UINT J = 0; j < num_properties; ++j) {
  if (all_items[j].id == 0x0112) {
    short orient;
    memcpy(&orient, all_items[j].value, sizeof(orient));

    if (orient == 3) {
      // RotateFlip(Rotate180FlipXY);
    }
    else if (orient == 6) {
      // RotateFlip(Rotate270FlipXY);
    }
    else if (orient == 8) {
      // RotateFlip(Rotate90FlipXY);
    }
  }
  break; // only orientation
}
```

## _Reference_
> [Reading and Writing Metadata](https://msdn.microsoft.com/en-us/library/windows/desktop/ms533832(v=vs.85).aspx)  
> [PropertyItem](https://msdn.microsoft.com/en-us/library/system.drawing.imaging.propertyitem.id(v=vs.110).aspx)
