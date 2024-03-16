[[深度学习基本概念]]
GAN可以work with  any  type of data,但其最popular的应用是产生图片.
系统由两部分组成:
1. generator  This is generative model itself 它take一个概率分布作为输入,尝试产生真是的输出图片.其purpose similar to VAE的decoder部分
2. discriminator 这部分take two alternating inputs:训练集的真实图片或generator 产生的samples. 它尝试确定图片是从real images中产生的还是generated ones
 trained together 
 discrimator尝试get better at distinguishing between the real 和fake images
 另一方面,generator tries to output realistic images so it could deceive the discriminator  into thinking that the generated image is real. 
 GAN still unsupervised since we don't need labels for the image
training gans

Our main goal is for the generator to produce realisitic images and the GAN framework is  a vehicle.
我们会先训练generator和discriminator seperately and sequentially, and alternate between the two phases 多次.
 引入一些notations:
 1. denote the generator with $G(z,\theta_g)$,   $\theta_g$是网络的weighs,$z$是latent vector.,serves as an input to the generator. think of it as a random seed value to kickstart the image-generation process. 这和VAE中的隐向量是类似的. z通常有一个概率分布,通常是random normal or random uniform. The generator outputs fake samples x ,with a probability distribution$p_g(x)$(real data according to generator)
 2. discriminator $D(x,\theta_d)$,其中$\theta_d$  是 网络的weights, it takes  as input either the real data with the $p(x)$ or the generated samples  
 3. 在训练过程中,我们denote the discriminator and generator loss functions with $J^D$ and $J^G$
GAN training different from the training pf a regular DNN ,because we have 2 networks. we can think of it as a sequential  minimax zero-sum game of two plauers(generator and discrinator)
Sequential:means that the players take turnns after one another , similar to chess or tic-tac-toe. 1,the discriminator tries to 最小化$J^D$