```
import torch
import torch.nn as nn

class Discriminator(nn.Module):
    def __init__(self, in_channels):
        super(Discriminator, self).__init__()
        self.model = nn.Sequential(
            nn.Conv2d(in_channels, 64, kernel_size=3, stride=2, padding=1),
            nn.LeakyReLU(0.2),
            nn.Conv2d(64, 128, kernel_size=3, stride=2, padding=1),
            nn.LeakyReLU(0.2),
            nn.Flatten(),
            nn.AdaptiveMaxPool2d(1),
            nn.Linear(128, 1)
        )
    
    def forward(self, x):
        x = self.model(x)
        return x

class Generator(nn.Module):
    def __init__(self, in_channels):
        super(Generator, self).__init__()
        self.model = nn.Sequential(
            nn.Linear(in_channels, 7 * 7 * in_channels),
            nn.LeakyReLU(0.2),
            nn.Unflatten(1, (in_channels, 7, 7)),
            nn.ConvTranspose2d(in_channels, 128, kernel_size=4, stride=2, padding=1),
            nn.LeakyReLU(0.2),
            nn.ConvTranspose2d(128, 128, kernel_size=4, stride=2, padding=1),
            nn.LeakyReLU(0.2),
            nn.Conv2d(128, 1, kernel_size=7, padding=3),
            nn.Sigmoid()
        )
        
    def forward(self, x):
        x = self.model(x)
        return x

```

```
import torch
import torch.nn as nn
from torch.utils.data import DataLoader
import numpy as np

class ConditionalGAN(nn.Module):
    def __init__(self, discriminator, generator, latent_dim):
        super(ConditionalGAN, self).__init__()
        self.discriminator = discriminator
        self.generator = generator
        self.latent_dim = latent_dim

    def forward(self, z, labels):
        return self.generator(z, labels)

    def train_step(self, images, labels, d_optimizer, g_optimizer, loss_fn, device):
        batch_size = images.size(0)
        # For real images
        real_labels = torch.ones(batch_size, 1).to(device)
        fake_labels = torch.zeros(batch_size, 1).to(device)

        # Move data to device
        images, labels = images.to(device), labels.to(device)

        # === Train Discriminator ===
        d_optimizer.zero_grad()
        # Loss for real images
        real_outputs = self.discriminator(images, labels)
        d_loss_real = loss_fn(real_outputs, real_labels)
        # Loss for fake images
        noise = torch.randn(batch_size, self.latent_dim).to(device)
        fake_images = self.generator(noise, labels)
        fake_outputs = self.discriminator(fake_images.detach(), labels)
        d_loss_fake = loss_fn(fake_outputs, fake_labels)
        # Combine losses
        d_loss = d_loss_real + d_loss_fake
        d_loss.backward()
        d_optimizer.step()

        # === Train Generator ===
        g_optimizer.zero_grad()
        # Generate fake images
        fake_images = self.generator(noise, labels)
        # Try to fool the discriminator
        fake_outputs = self.discriminator(fake_images, labels)
        g_loss = loss_fn(fake_outputs, real_labels)
        g_loss.backward()
        g_optimizer.step()

        return d_loss.item(), g_loss.item()

# 假设已经定义了d_optimizer, g_optimizer, loss_fn, dataset_loader
device = torch.device("cuda" if torch.cuda.is_available() else "cpu")
cond_gan = ConditionalGAN(discriminator, generator, latent_dim).to(device)

# 假设dataset_loader是用DataLoader加载的数据集
epochs = 50
for epoch in range(epochs):
    for images, labels in dataset_loader:
        d_loss, g_loss = cond_gan.train_step(images, labels, d_optimizer, g_optimizer, loss_fn, device)
    
    print(f"Epoch {epoch}, Discriminator Loss: {d_loss}, Generator Loss: {g_loss}")

```

```
device = torch.device("cuda" if torch.cuda.is_available() else "cpu")

# 初始化模型
cond_gan = ConditionalGAN(discriminator=discriminator, generator=generator, latent_dim=latent_dim)
cond_gan.to(device)

# 设置训练模式
cond_gan.train()

# 训练周期
epochs = 20

for epoch in range(epochs):
    for images, labels in dataset:
        # 将数据移动到正确的设备
        images, labels = images.to(device), labels.to(device)
        
        # 执行训练步骤
        d_loss, g_loss = cond_gan.train_step(images, labels, d_optimizer, g_optimizer, loss_fn, device)
    
    print(f"Epoch {epoch}: Discriminator Loss: {d_loss}, Generator Loss: {g_loss}")

```


```
import numpy as np
import imageio
import torchvision.transforms as transforms
from PIL import Image

# 假设 fake_images 是上一步生成的图像张量
# 将图像数据缩放到 [0, 255] 并转换为 numpy 数组
fake_images = fake_images * 255.0
fake_images_np = fake_images.cpu().detach().numpy().astype(np.uint8)

# 转换图像大小为 (96, 96)
# 我们需要遍历每个图像并调整大小
resized_images = []
for img in fake_images_np:
    img = np.squeeze(img)  # 去除通道维度，如果图像是灰度的
    img_pil = Image.fromarray(img)  # 转换为 PIL 图像以便调整大小
    img_resized = img_pil.resize((96, 96), Image.BILINEAR)  # 调整图像大小
    resized_images.append(np.array(img_resized))

# 使用 imageio 保存动画
imageio.mimsave('animation.gif', resized_images, fps=1)

# 由于当前环境可能不支持直接嵌入或显示文件，
# 下面是将文件保存到可下载路径的代码示例：
save_path = '/mnt/data/animation.gif'  # 确保路径存在或已正确设置
imageio.mimsave(save_path, resized_images, fps=1)

# 提供下载链接
save_path

```