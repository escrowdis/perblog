---
#layout: post
title: "Quaternion Operation & 3D Rotation"
date: 2017-07-08 13:47
author: escrowdis
comments: true
tags: [quaternion, 3d rotation, unit quaternion, angular velocity]
---
<script type="text/javascript" async src="//cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-MML-AM_CHTML">
</script>

# Preface
This article is going to briefing how to use quaternion in three dimension rotation.

If you want detailed information and definition about it, please check the links shown below!
[Wiki](https://en.wikipedia.org/wiki/Quaternion) & [wiki rotation](https://en.wikipedia.org/wiki/Quaternions_and_spatial_rotation).

# Basic definition

### Operation

$i^2 = j^2 = k^2 = ijk = -1$

$ij = k, jk = i, ki = j$

$ji = -k, kj = -i, ik = -j$

|       |  1  |  i  |  j  |  k  |
|-------| --- | --- | --- | --- |
| **1** |  1  |  i  |  j  |  k  |
| **i** |  i  | -1  |  k  | -j  |
| **j** |  j  | -k  | -1  |  i  |
| **k** |  k  |  j  | -i  | -1  |

$q = (s, v) = s + v_{x} \vec{i} + v_{y} \vec{j} + v_{z} \vec{k}$

where $s$ is the **scalar part** and the $v$ is the **vector part**
(rotation notation about coordinates x, y and z).

$q_w = \cos(\theta / 2)$

$q_x = \sin(\theta / 2) \vec{v_u}_x$

$q_y = \sin(\theta / 2) \vec{v_u}_y$

$q_z = \sin(\theta / 2) \vec{v_u}_z$

### Conjugate

$q^* = \bar{q} = (s, -v) = s - v_{x} \vec{i} - v_{y} \vec{j} - v_{z} \vec{k}$

### Inverse

$q^{-1} = \frac{ q^* }{ ||q|| }$

### Non-commutative

$q = q_1 q_2 \neq q_2 q_1$

---

# 3D Rotation

## Vector Rotated by Quaternion

If you want to rotate a vector $\vec{v} = (v_x, v_y, v_z)$ by quaternion, it can be like this:

$p' = qpq^{-1}$

**Example**: If we want to rotate a vector $90^\circ$ by coordinate $z+$, so

$\vec{v} = (1, 1, 1)$ and $q = (0.707, 0, 0, 0.707)$.

It comes from,
**Rotated angle**: $\theta = 90^\circ * \frac{\pi}{180}$

**Rotation Notation**: $n = (0, 0, 1)$

$q_w = 0.707 = \cos(\frac{\theta}{2})$

$q_x = 0 = \sin(\frac{\theta}{2}) * 0$

$q_y = 0 = \sin(\frac{\theta}{2}) * 0$

$q_z = 0.707 = \sin(\frac{\theta}{2}) * 1$

**Note: It's OK if quaternion is not unit**

So the answer is

$p' = (-1, 1, 1)$,

which is calculated using Eigen::Quaterniond in C++

```c++
#include <iostream>

#include <eigen3/Eigen/Core>
#include <eigen3/Eigen/Geometry>

int main() {
    Eigen::Quaterniond vec(0, 1, 1, 1);
    Eigen::Quaterniond q_rot_z(0.707, 0, 0, 0.707);
    Eigen::Quaterniond vec_rot;
    vec_rot = q_rot_z * vec * q_rot_z.inverse();
    std::cout << "Output is: " << vec_rot.x() << " " <<
                 vec_rot.y() << " " << vec_rot.z() << std::endl;
}
```

## Between Quaternions

In 3 dimension rotation, the operation between two quaternion must be **UNIT quaternion ($q_u$)**
which is a.k.a. normalized shown below:

$q_u = \frac{ q }{ ||q|| } = (q_w, q_x, q_y, q_z)$ and  $||q_u|| = 1$.

Here's an **example**:

$\vec{v} = (v_x, v_y, v_z)$

$\vec{v_u} = \frac{ \vec{v} }{ ||\vec{v}|| }$

$q_w = \cos(\theta / 2)$

$q_x = \sin(\theta / 2) \vec{v_u}_x$

$q_y = \sin(\theta / 2) \vec{v_u}_y$

$q_z = \sin(\theta / 2) \vec{v_u}_z$

$||q|| = \sqrt{ q q^* } = 1$

And the equation below is that **q will be rotated by $\Delta{q}$ based on q's coordinate and all the quaternion is UNIT**

$$q' = q * \Delta{q}$$

If the quaternion will be estimated by angular velocity ($\omega$), the equation will be

$\omega_u = \frac{ \omega }{ ||\omega|| }$

$\Delta{q} = (1, \frac{ \Delta{t} }{ 2 } (\omega_{u}))$

Before multiplication, please normalize it first.

- - -

TBD.
