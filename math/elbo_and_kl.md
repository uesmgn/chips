## Variational Autoencoder

データ$x$ の集合;トレーニングセットが与えられたとき、Variational Autoencoderでは対数尤度$\log p_*(x)$を最大化させる。



### 変分下限, Evidence Lower Bound; ELBO

$$
\begin{aligned}
\log{p_*(x)}&=\log{\int p_*(x,z)dz}\\
&=\log{q_\phi(z|x)\frac{p_*(x,z)}{q_\phi(z|x)}dz}\\
&\ge\int{q_\phi(z|x)\log{\frac{p_*(x,z)}{q_\phi(z|x)}}dz}~(~\because~\mathrm{Jensen's~ inequality}~)\\
&=L(x,z);~\mathrm{ELBO~(~Evidence~Lower~Bound~)}
\end{aligned}
$$

$$
\begin{aligned}
\log{p_*(x)}-L(x,z)&=
\log p_*(x)-\int{q_\phi(z|x)\log{\frac{p_*(x,z)}{q_\phi(z|x)}}}dz\\
&=\log{p_*(x)}\int{q_\phi(z|x)}dz-\int{q_\phi(z|x)\log{\frac{p_*(x,z)}{q_\phi(z|x)}}}dz\\
&=\int{q_\phi(z|x)\log{p_*(x)}}dz-\int{q_\phi(z|x)\log{\frac{p_*(x)p_\theta(z|x)}{q_\phi(z|x)}}}dz\\
&=\int{q_\phi(z|x)\log{\frac{q_\phi(z|x)}{p_\theta(z|x)}}}dz\\
&=D_{KL}[q_\phi(z|x)||p_\theta(z|x)]\\
&=\bold{E}_{q_\phi(z|x)}[\log{q_\phi(z|x)-\log{p_\theta(z|x)}}]\\
&=\bold{E}_{q_\phi(z|x)}[\log{q_\phi(z|x)-\log{\frac{p(z)p_\theta(x|z)}{p_*(x)}}}]\\
&=\bold{E}_{q_\phi(z|x)}[\log{q_\phi(z|x)-\log{\frac{p(z)p_\theta(x|z)}{p_*(x)}}}]\\
&=\bold{E}_{q_\phi(z|x)}[\log{\frac{q_\phi(z|x)}{p(z)}-\log{p_\theta(x|z)}}]+\log{p_*(x)}\int{q_\phi(z|x)}dz\\
&=D_{KL}[q_\phi(z|x)||p(z)]-\bold{E}_{q_\phi(z|x)}[\log{p_\theta(x|z)}]+\log{p_*(x)}
\end{aligned}
$$

$$
\begin{aligned}
\therefore L(x,z)&=-D_{KL}[q_\phi(z|x)||p(z)]+\bold{E}_{q_\phi(z|x)}[\log{p_\theta(x|z)}]
\end{aligned}


$$

$$
p(z)=\mathcal{N}(0,I)
$$

- ニューラルネットワークの出力$q_\theta(z|x)$を多次元正規分布に従わせることで$KL$ダイバージェンス$D_{KL}[q_\phi(z|x)||p(z)]$を小さく
  
  → 正規分布同士のKLダイバージェンス , Reparametrization trick

- $q_\phi(z|x)$に関する$\log{p_\theta(x|z)}$の期待値を最大化
  
  → Binary Cross Entropy Loss
  
  $\because x$は多変量ベルヌーイ分布に従う
  
  (各ピクセルの値 $x_i$は0~1→各ピクセルが1 である確率)




























