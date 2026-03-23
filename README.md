# Burgers-Equation---Test
We consider a class of nonlinear hyperbolic conservation laws, posed in one spatial dimension, of the general form

$ u_{t}+\partial_{x}f(u)=s(x,t,u),\quad (x,t)\in\Omega\times(0,T] $

$ u_{t}+\partial_{x}f(u)=s(x,t,u),\quad (x,t)\in\Omega\times(0,T] $

where $u(x,t)$ denotes the unknown scalar field, f(u) is a nonlinear flux function which is set to $u^{2}/2$ throughout this section until mentioned explicitly, and $s(x,t,u)$ represents a source/sink term.

This benchmark is designed to isolate a fundamental limitation of baseline PINNs for nonlinear hyperbolic problems. The initial condition is smooth, no source term is present, and the only difficulty arises from finite-time shock formation induced by nonlinear flux. 

Let $\Omega=[-1,1]$ be a bounded spatial domain with boundary $\partial\Omega$ , and $\mathcal{Q}:=\Omega\times(0,0.5]$ denote the corresponding space-time domain.

As a specific instance of the general Burgers equation, we are setting the source term to zero, i.e., $s(x,t,u)\equiv0$. The problem is supplemented with the smooth initial condition $$u_{0}(x)=\sin(\pi x),\qquad x\in\Omega.$$ 
Although the initial data is smooth, the initial slope leads to finite-time gradient blow-up and the formation of a shock at $x=0.$
At t=0, both neural approximations accurately reproduce the prescribed smooth initial condition, indicating correct enforcement of the initial constraint and comparable approximation capability in the absence of discontinuities.

At the later time $t=0.5$, after shock formation, the behaviour of the two methods differs markedly. The baseline PINN exhibits non-physical oscillations and overshoots in the vicinity of the shock. This behaviour reflects the absence of intrinsic stabilization and explicit discontinuity treatment in standard residual-based PINN formulations, which implicitly favour smooth solutions through global $L_{2}$ minimization.

In contrast, the FC-PINN sharply resolves the shock location while preserving monotonicity across the discontinuity. The flux-corrected formulation suppresses spurious oscillations without introducing excessive numerical diffusion, resulting in close agreement with the exact entropy solution. Quantitatively, the global space–time $L_{2}$ error is reduced from $1.305\times10^{-1}$ for the baseline PINN to $8.97\times10^{-3}$ for the FC-PINN, corresponding to an improvement of approximately $93.1\%.$

