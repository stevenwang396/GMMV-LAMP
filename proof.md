\appendix[Derivation of MMSE Denoiser]\label{AppendixA}

Consider the denoising problem for the signal model given by
\begin{equation}\label{appendix1} % eq.32
	\tilde{\mathbf{x}}=\bar{\mathbf{x}} +\mathbf{\Sigma}^{\frac{1}{2}}\mathbf{n},
\end{equation}
where $\tilde{\mathbf{x}}$ and $\bar{\mathbf{x}}\in \mathbb{C} ^{K\times 1}$ denote the noisy and noiseless signals, respectively, $\mathbf{n}\in \mathbb{C}^{K\times 1}\sim\mathcal{CN}(\mathbf{0},\mathbf{I})$ is an AWGN vector, and $\mathbf{\Sigma}=\mathrm{diag}\left(\left[\sigma^{2}[1],\sigma^{2}[2],\ldots,\sigma^{2}[K]\right]\right)$ is the diagonal matrix depicting the noise power with $\sigma^{2}[k]\ge0,\forall k\in\{1,2,\ldots,K\}$. Because the support across different subcarriers appears or disappears at the same time, $\bar{\mathbf{x}}$ follows a Bernoulli-Gaussian distribution as $(1-\gamma )\delta_{0}+\gamma p_{\mathbf{h}_{\epsilon}}$. Here, $\delta_{0}$ denotes the point mass measure at zero and $p_{\mathbf{h}_{\epsilon}}$ denotes the distribution of $\mathbf{h}_{\epsilon}\sim\mathcal{CN}(\mathbf{0},\epsilon\mathbf{I})$. 

In this way, the probability when $\tilde{\mathbf{x}}=\mathbf{x}'=\mathbf{h}_{\epsilon}+\mathbf{\Sigma}^{\frac{1}{2}}\mathbf{n}$ is $\gamma$, and the probability is $1-\gamma$ when $\tilde{\mathbf{x}}=\mathbf{\Sigma}^{\frac{1}{2}}\mathbf{n}$. According to standard estimation theory, defining $\boldsymbol{\Theta} = \mathrm{diag}\bigg(\frac{1}{\epsilon+\sigma^{2}[1]},\ldots,\frac{1}{\epsilon+\sigma^{2}[K]}\bigg)$ the mean and covariance matrix of $\mathbf{h}_{\epsilon}$ can be computed respectively as 
\begin{align}\label{appendix2} % eq.33
	\mathbb{E}[\mathbf{h}_{\epsilon}|\mathbf{x}'=\mathbf{x}] =& \epsilon\boldsymbol{\Theta}\mathbf{x},\\
	\mathbb{E}[\mathbf{h}_{\epsilon}\mathbf{h}_{\epsilon}^{\rm H}|\mathbf{x}'=\mathbf{x}] =& \epsilon \mathbf{I} - \epsilon^{2}\boldsymbol{\Theta}+\epsilon^{2}\boldsymbol{\Theta}\mathbf{x}\mathbf{x}^{\rm H}\boldsymbol{\Theta}.
\end{align}
Furthermore, we can compute the mean of $\bar{\mathbf{x}}$ as
\begin{align}\label{appendix4} % eq.35
	\mathbb{E}[\bar{\mathbf{x}}|\hat{\mathbf{x}}=\hat{\mathbf{x}}'] &= \int \bar{\mathbf{x}}p_{\mathbf{x}|\hat{\mathbf{x}}}(\bar{\mathbf{x}}=\mathbf{x}|\hat{\mathbf{x}}=\hat{\mathbf{x}}')\mathrm{d}\mathbf{x} \nonumber  \\ &\hspace*{-20mm}= \frac{1}{p_{\hat{\mathbf{x}}}}\int p_{\mathbf{x}|\hat{\mathbf{x}}}(\bar{\mathbf{x}}=\mathbf{x}|\hat{\mathbf{x}}=\hat{\mathbf{x}}')(\gamma p_{\mathbf{h}_{\epsilon}}(\mathbf{h}_{\epsilon}=\mathbf{x})+(1-\gamma)\delta_{0}(\mathbf{x}))\mathrm{d}\mathbf{x} \nonumber \\
	& = \frac{\gamma p_{\mathbf{x}'}(\mathbf{x}'=\hat{\mathbf{x}}')}{p_{\hat{\mathbf{x}}}(\hat{\mathbf{x}}=\hat{\mathbf{x}}')p_{\mathbf{x}'}(\mathbf{x}'=\hat{\mathbf{x}}')}\mathbb{E}[\mathbf{h}_{\epsilon}|\mathbf{x}'=\hat{\mathbf{x}}'],
\end{align}

By defining 
$ \phi(\hat{\mathbf{x}}) = \frac{1}{1+\frac{1-\gamma}{\gamma}e^{-\hat{\mathbf{x}}^{\rm H}\mathbf{P}\hat{\mathbf{x}}}\prod_{k=1}^{K}(1+\frac{\epsilon}{\sigma^{2}[k]}) }
$ and $
\mathbf{P} = \mathrm{diag}\left(\frac{\epsilon}{\sigma^{2}[1](\sigma^{2}[1]+\epsilon)},\ldots,\frac{\epsilon}{\sigma^{2}[K](\sigma^{2}[K]+\epsilon)}\right) ,
$
the shrinkage function $\bm{\eta}_{\rm CS}(\hat{\mathbf{x}}';\gamma,\epsilon,\mathbf{\Sigma})$ can be rewritten as 
\begin{equation}\label{appendix7} % eq.38
	\bm{\eta}_{\rm CS}(\hat{\mathbf{x}}';\gamma,\epsilon,\mathbf{\Sigma})=\mathbb{E}[\mathbf{x}|\hat{\mathbf{x}} = \hat{\mathbf{x}}']=\phi(\hat{\mathbf{x}}')\boldsymbol{\Theta}\hat{\mathbf{x}}'.
\end{equation}

It should be noted that when taking the derivative of \eqref{appendix7}, we can approximate $\phi(\hat{\mathbf{x}})$ as a constant since the dimension of $\hat{\mathbf{x}}$ is quite large, and the derivative becomes $\frac{\epsilon\phi(\hat{\mathbf{x}})}{\epsilon+\sigma^{2}[k]}$.
