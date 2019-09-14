# 阅读总结

> 注意：
> 1. 代码里的状态是 nominal/true state, 协方差是 error state 的 conv，虽然状态转移和更新都应该是对 error state 操作的，但代码里只是用临时变量存储，甚至状态转移压根就没计算 error state（直接根据 nominal state 的状态转移计算），计算出来后就直接怼到 nominal state 中
> 2. 外参、bias、g 都是在 update 阶段更新的，预测阶段只更新 qvp 状态

TODO:

1. 卡方检验
2. processModel 中对 $\Phi$ 的部分项有修改，还没明白原理（参考 [1] 得知跟 [2,3] 能观性约束有关）
3. predictNewState 中 runge-kutta 积分关于 k3_v_dot 和 k2_q 跟我推的不一样，感觉是我推得有问题，但又没找到在哪
4. measurementJacobian 中 $\frac{\partial^{C_{i,1}}\bold{p}_j}{\partial \bold{x}_{C_{i,1}}}$ 对四元数的偏导还不知道怎么推，其他地方在 stateAugmentation 中的 J 也有类似的偏导
5. measurementJacobian 中 observability constrain 作用不明（能观性约束）
6. removeLostFeatures 中把初始化后的 feature 都删了，为什么在 publish 中还有已初始化的 feature？
7. 2point-ransac 没看

## reference

1. [TurtleZhong/msckf_mono](https://github.com/TurtleZhong/msckf_mono)
2. On the consistency of Vision-aided Inertial Navigation
3. Consistency Analysis and Improvement of Vision-aided Inertial Navigation
4. [UMiNS/MSCKF_VIO_MONO](https://github.com/UMiNS/MSCKF_VIO_MONO)
