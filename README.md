# time-dependent-heat

🔥 README — 3D Heat Equation Solver (Simple Version)

This project solves the time-dependent heat equation in 3D using a finite-difference method:

𝑢
𝑡
=
𝛼
∇
2
𝑢
u
t
	​

=α∇
2
u

We evolve a temperature field forward in time starting from an initial hot plane at 
𝑥
=
0
x=0.

How It Works

The domain is a 3D grid with size (nx, ny, nz).

Temperature is stored in a NumPy array u.

At each time step, we update the interior points using the discrete Laplacian:

∇
2
𝑢
≈
𝑢
𝑖
+
1
,
𝑗
,
𝑘
+
𝑢
𝑖
−
1
,
𝑗
,
𝑘
+
𝑢
𝑖
,
𝑗
+
1
,
𝑘
+
𝑢
𝑖
,
𝑗
−
1
,
𝑘
+
𝑢
𝑖
,
𝑗
,
𝑘
+
1
+
𝑢
𝑖
,
𝑗
,
𝑘
−
1
−
6
𝑢
𝑖
,
𝑗
,
𝑘
∇
2
u≈u
i+1,j,k
	​

+u
i−1,j,k
	​

+u
i,j+1,k
	​

+u
i,j−1,k
	​

+u
i,j,k+1
	​

+u
i,j,k−1
	​

−6u
i,j,k
	​


The update rule (explicit Euler) is:

𝑢
𝑛
+
1
=
𝑢
𝑛
+
𝛼
 
𝑑
𝑡
 
∇
2
𝑢
𝑛
u
n+1
=u
n
+αdt∇
2
u
n
Running the Solver

Example usage:

from heat import solve_heat

cfg = {
    "nx": 50, "ny": 50, "nz": 50,
    "dt": 1e-4,
    "steps": 500
}

u = solve_heat(cfg)

Initial Condition

The plane at x = 0 is set to temperature 1.0:

u[0,:,:] = 1.0


Everything else starts at 0.

Output

The function returns the final 3D temperature field:

u.shape  # (nx, ny, nz)


You can slice or visualize it however you like.

File

heat.py — main solver
