# Chapter 0: Overview

In *Ray Tracing In One Weekend*, you built a simple brute force path tracer. In this installment we’ll add textures, volumes (like fog), rectangles, instances, lights, and support for lots of objects using a BVH. When done, you’ll have a “real” ray tracer.

在[Ray Tracing In One Weekend]([http://www.realtimerendering.com/raytracing/Ray%20Tracing%20in%20a%20Weekend.pdf](http://www.realtimerendering.com/raytracing/Ray Tracing in a Weekend.pdf))这本书中，你实现了一个简单粗暴的路径追踪。在这本书中，我们将引入纹理，体积（如雾），立方体，实例，灯光和支持层次包围的大量物体。当你实现这些之后，你将会得到一个"真正的"光线追踪。

A heuristic in ray tracing that many people-- including me-- believe, is that most optimizations complicate the code without delivering much speedup. What I will do in this mini-book is go with the simplest approach in each design decision I make. Check www.in1weekend.com for readings and references to a more sophisticated approach. However, I strongly encourage you to do no premature optimization; if it doesn’t show up high in the execution time profile, it doesn’t need optimization until all the features are supported! 

包括我在内的许多人都相信——对于光线追踪的启发式优化方法会使得代码复杂化，而不会提供太多的加速。在这本小书中，我将要做的是在每个设计决策中采用最简单的方法。请访问www.in1weekend.com获取阅读材料，并参考更加复杂的方法。但是，我强烈建议你不要过早的优化。如果它的运行时间没有很高，那么在支持所有功能之前并不需要进行优化。

The two hardest parts of this book are the BVH and the Perlin textures. This is why the title suggests you take a week rather than a weekend for this endeavor. But you can save those for last if you want a weekend project. Order is not very important for the concepts presented in this book, and without BVH and Perlin texture you will still get a Cornell Box! 

这本书的两个难点在于层次包围盒（Bounding volume hierarchy，BVH）和柏林（噪声）纹理。这就是书名建议你花费一周时间而不是一个周末的时间实现本书内容的原因。但是如果你想在一个周末实现这个项目，你可以省略这两个难点。对于本书提出的概念而言，顺序显得并不是那么重要。除此之外，如果你没有实现BVH和柏林纹理，你依然可以获得一个康奈尔盒！

**Acknowledgments**: Thanks to Becker for his many helpful comments on the draft and to Matthew Heimlich for spotting a critical motion blur error. Thanks to Andrew Kensler, Thiago Ize,and Ingo Wald for advice on ray-AABB tests. Thanks to David Hart and Grue Debry for help with a bunch of the details. Thanks to Jean Buckley for editing.

**鸣谢：**感谢Becker对于本书草稿的许多有用的评论；感谢Matthew Heimlich发现了一个关键的运动模糊错误；感谢Andrew Kensler，Thiago Ize和Ingo Wald对于ray-AABB测试的建议；感谢David Hart和Grue Debry对于一堆细节的帮助；感谢Jean Buckley的编辑。