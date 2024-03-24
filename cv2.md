OpenCV（cv2）是一个功能强大的计算机视觉库，提供了许多基本函数用于图像处理、计算机视觉和机器学习任务。以下是一些常用的基本函数：

1. `cv2.imread()`: 用于读取图像文件并将其加载为NumPy数组。
 ```python
image_path = 'P2_No23.jpg'
image = cv2.imread(image_path)

image_path = os.path.join(folder_path, image_file)
image = cv2.imread(image_path)

image = cv2.imread(os.path.join(folder_path, filename))
```  
2. `cv2.imshow()`: 在窗口中显示图像。
```python
cv2.imshow('Image', rotated_image)
```
3. `cv2.imwrite()`: 将图像保存为文件。
```python
result_filename = os.path.join(result_path, filename)
cv2.imwrite(result_filename, test_image)

detected_circles_filename = os.path.splitext(original_img_filename)[0] + '.jpg'
cv2.imwrite(os.path.join('D:/A8/Reconnaissance/Part 1 Result',detected_circles_filename), dst)
```
4. `cv2.cvtColor()`: 用于图像颜色空间的转换，如BGR到灰度、BGR到RGB等。
```
gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
```
5. `cv2.resize()`: 用于调整图像大小。
```python
resized_image = cv2.resize(image, (200, 300))
resized_image = cv2.resize(image, (new_width, new_height))
```
6. `cv2.flip()`: 用于在水平或垂直方向上翻转图像。

7. `cv2.merge()` 和 `cv2.split()`: 用于多通道图像的合并和分离。

8. `cv2.rectangle()`: 在图像上绘制矩形。
```python
cv2.rectangle(image, (x, y), (x + w, y + h), (0, 255, 0), 2)
```
9. `cv2.circle()`: 在图像上绘制圆。
```python
cv2.circle(dst, center, radius, (0, 255, 0), 2)
```
10. `cv2.line()`: 在图像上绘制直线。
```python
cv2.line(resized_image, (0, 0), (89, 85), (0, 255, 0), 2)
```
11. `cv2.putText()`: 在图像上绘制文本。
```python
cv2.putText(resized_image, f'color: {color}', (x, y - 10),
                cv2.FONT_HERSHEY_SIMPLEX, 0.5, (0, 255, 0), 2)
```
12. `cv2.threshold()`: 用于图像阈值化。

13. `cv2.findContours()`: 用于在二值图像中查找轮廓。
```python
contours, _ = cv2.findContours(
    edges, cv2.RETR_EXTERNAL, cv2.CHAIN_APPROX_SIMPLE)
```
14. `cv2.drawContours()`: 在图像上绘制轮廓。
```python
cv2.drawContours(imgContour, cnt, -1, (255, 0, 0), 3)
```
15. `cv2.bitwise_and()`, `cv2.bitwise_or()`, `cv2.bitwise_not()`, `cv2.bitwise_xor()`: 用于图像的按位逻辑操作。

这些函数只是 OpenCV 中可用函数的一小部分，但它们是构建图像处理和计算机视觉应用程序的基础。



```python
h,w,c = img.shape
#图像大小为128*128*3
print(h,w,c)
#OpenCV的读取顺序为B，G，R: 128 128 3

print(img.size) # 访问图像的总像素数
```
```python
for rect in possible_rectangles:
    # 获取矩形的外接矩形
    x, y, w, h = cv2.boundingRect(rect)
    # 提取矩形区域
    roi = resized_image[y:y+h, x:x+w]

```    
```python
if a > c and b > d:
    # 需要将图片向右旋转 90 度
    rotated_image = cv2.rotate(resized_image, cv2.ROTATE_90_CLOCKWISE)
elif a < c and b < d:
    # 需要将图片向左旋转 90 度
    rotated_image = cv2.rotate(resized_image, cv2.ROTATE_90_COUNTERCLOCKWISE)
elif a > c and b < d:
    # 需要将图片旋转 180 度
    rotated_image = cv2.rotate(resized_image, cv2.ROTATE_180)
else:
    # 图片已经在正确的方向上，无需旋转
    rotated_image = resized_image
```