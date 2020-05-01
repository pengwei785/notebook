PyTorch
=======

Pytorch和TensorFlow速度测试::

   import torch
   import tensorflow as tf
   import time
   import numpy as np
   def himmelblau(x):
       return (x[0]**2 + x[1] - 11)**2 + (x[0] + x[1]**2 - 7)**2
   import plotly.graph_objects as go
   x = np.arange(-6, 6, 0.1)
   y = np.arange(-6, 6, 0.1)
   # print('x,y range:', x.shape, y.shape)
   X, Y = np.meshgrid(x, y)
   fig = go.Figure(data=go.Surface(z=himmelblau([X,Y])))
   fig.write_image('figure2.svg')
   fig.write_html('first_figure.html', auto_open=True)
   tic = time.time()
   x = torch.tensor([0., 0.], requires_grad=True)
   optimizer = torch.optim.Adam([x], lr=1e-3)
   for step in range(20000):
       pred = himmelblau(x)
       optimizer.zero_grad() # 梯度信息清零
       pred.backward()
       optimizer.step() # 每调用一次step，就更新一次: x' = x, y' = y
       
       if step % 2000 == 0:
           print('step{}: x = {}, f(x) = {}'.format(step, x.detach().numpy(), pred.item()))
   toc = time.time()
   print('time:',toc-tic)
   tic = time.time()
   x = tf.Variable([0., 0.])  # 传入GradientTape计算梯度的必须是tf.Variable类型
   optimizer = tf.optimizers.Adam(lr=1e-3)
   for step in range(20000):
       with tf.GradientTape() as tape:
           tape.watch([x])
           pred = himmelblau(x)
           
       grads = tape.gradient(pred, [x])
       optimizer.apply_gradients(zip(grads, [x])) # 和pytorch不同，tf是将所有梯度信息存起来一次性更新
       # x -= 0.001*grads
       
       if step % 2000 == 0:
           print('step{}: x = {}, f(x) = {}'.format(step, x.numpy(), pred.numpy()))
   toc = time.time()
   print('time:',toc-tic)