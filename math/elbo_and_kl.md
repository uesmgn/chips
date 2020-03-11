## Variational Autoencoder

データ$x$ の集合;トレーニングセットが与えられたとき、Variational Autoencoderでは確率密度関数$p(x)$を最大化させる。

ここで，

$p(x)=\int{p(z)p_\theta(x|z)}dz$

対数をとって，

$\log{p(x)}=\log[\int{p(z)p_\theta(x|z)}dz]\ge\int{p(z)\log{p_\theta(x|z)}dz}\ (\mathrm{Jensenの不等式より})$











### 変分下限, Evidence Lower Bound; ELBO


