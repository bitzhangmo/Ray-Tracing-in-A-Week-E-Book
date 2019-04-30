# Chapter 1: Motion Blur 运动模糊

When you decided to ray trace, you decided visual quality was worth more run-time. In your fuzzy reflection and defocus blur you needed multiple samples per pixel. Once you have taken a step down that road, the good news is that almost all effects can be brute-forced. Motion blur is certainly one of those. In a real camera, the shutter opens and stays open for a time interval, and the camera and objects may move during that time. Its really an average of what the camera sees over that interval that we want. We can get a random estimate by sending each ray at some random time when the shutter is open. As long as the objects are where they should be at that time, we can get the right average answer with a ray that is at exactly a single time. This is fundamentally why random ray tracing tends to be simple. 

当你决定做光线追踪的时候，你认为花更多的运行来追求更好的视觉效果是值得的。在模糊反射和离焦模糊中，每个像素需要多重采样。一旦你走上了这条道路，好消息是几乎所有的效果都可以被不计代价的实现。毫无疑问，运动模糊是其中的一种。在真实世界的相机中，快门打开并且保持打开一段时间，并且在此期间相机和物体可能会移动。它实际上是相机在我们想要的间隔上看到的平均值。我们可以通过在快门打开时的某个随机时间发射光线来获得随机估计。只要目标对象在那个时候确实位于它们应该在的位置，我们就能用一条恰好一次的光线得到正确的平均结果。这基本上是随机光线追踪趋于简单的原因。

The basic idea is to generate rays at random times while the shutter is open and intersect the model at that one time. The way it is usually done is to have the camera move and the objects move, but have each ray exist at exactly one time. This way the “engine” of the ray tracer can just make sure the objects are where they need to be for the ray, and the intersection guts don’t change much. 

基本思想是在快门打开的时候随机生成光线，并且在这个时候与模型相交。通常的做法是让相机移动并移动物体，但是每条射线近存在一次。通过这种方式，光线追踪器的"引擎"可以确保物体是光线所需的位置，并且交叉口的内径不会发生太大变化。

For this we will first need to have a ray store the time it exists at: 

为此，我们首先需要一个光线存储它存在的时间：

```cpp
class ray
{
  public:
  	ray() {}
  
}
```

