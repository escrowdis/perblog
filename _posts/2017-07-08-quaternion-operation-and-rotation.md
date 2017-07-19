---
#layout: post
title: "Quaternion Operation & 3D Rotation"
date: 2017-07-08 13:47
author: escrowdis
comments: true
tags: [quaternion, 3d rotation, unit quaternion, angular velocity]
---
Preface
---
This article is going to tell how to use quaternion to describe rotation in 3 dimension.

If you need detailed definition and information, please go check
[Wiki](https://en.wikipedia.org/wiki/Quaternion) &
[wiki rotation](https://en.wikipedia.org/wiki/Quaternions_and_spatial_rotation).

# Basic definition
### Operation
$i^2 = j^2 = k^2 = -1$

$ij = k, jk = i, ki = j$

$ji = -k, kj = -i, ik = -j$

|       |  1  |  i  |  j  |  k  |
|-------| --- | --- | --- | --- |
| **1** |  1  |  i  |  j  |  k  |
| **i** |  i  |  -1 |  k  |  -j |
| **j** |  j  |  -k |  -1 |  i  |
| **k** |  k  |  j  |  -i |  -1 |

$q = (s, v) = s + v_{x} \vec{i} + v_{y} \vec{j} + v_{z} \vec{k}$

### Conjugate
$q^* = \bar{q} = (s, -v) = s - v_{x} \vec{i} - v_{y} \vec{j} - v_{z} \vec{k}$

### Inverse
$q^{-1} = \frac{q^*}{||q||}$

### Non-commutative
$q = q_{1} q_{2} \neq q_{2} q_{1}$

---

# 3D Rotation
In rotation, all the quaternion should be used in **UNIT** quaternion
which means:

$q_u = \frac{q}{||q||} = (q_w, q_x, q_y, q_z)$

$\vec{v} = (v_x, v_y, v_z)$

$\vec{v_u} = \frac{\vec{v}}{||\vec{v}||}$

$q_{w} = \cos(\theta / 2)$

$q_{x} = \sin(\theta / 2) \vec{v_u}_x$

$q_{y} = \sin(\theta / 2) \vec{v_u}_y$

$q_{z} = \sin(\theta / 2) \vec{v_u}_z$

$||q|| = \sqrt{q q^*} = 1$

And the equation below is that **q will be rotated by $\Delta{q}$ based on q's coordinate and all the quaternion is UNIT**

$q' = q * \Delta{q}$

If the quaternion will be estimated by angular velocity ()$\omega$), the equation will be

$\omega_{u} = \frac{\omega}{||\omega||}$

$\Delta{q} = (1, \frac{\Delta{t}}{2} (\omega_{u}))$

Before multiplication, please normalize it first.

TBD.
