## 行内与独行

| 说明              | 语法         | 用例  |
| -----------------| ------------ | ----- |
| 行内公式：将公式插入到本行内 | `$公式内容$` |$xyz$|
| 独行公式：将公式插入到新的一行内，并且居中（需换行） | `$$公式内容$$` | -     |

> $$
> xyz
> $$
> ```
> $$
> xyz
> $$
> ```

## 上标、下标与组合

| 说明 | 语法 | 用例 |用例源码|
| ---- | ---- | ---- | ---- |
| 上标符号 | `^` |$x^4$|`$x^4$`|
|下标符号|`_`|$x_1$|`$x_1$`|
|组合符号|`{}`|${16}_{8}O{2+}_{2}$|`${16}_{8}O{2+}_{2}$`|

## 汉字、字体与格式

| 说明 | 语法 | 用例 |用例源码|
| ---- | ---- | ---- | ---- |
| 汉字形式 | `\mbox{}` |$V_{\mbox{初始}}$|`$V_{\mbox{初始}}$`|
|字体控制|`\displaystyle`|$\displaystyle\frac{x+y}{y+z}$|`$\displaystyle\frac{x+y}{y+z}$`|
|下划线符号|`\underline`|$\underline{x+y}$|`$\underline{x+y}$`|
|标签|`\tag{数字}`|-|`$$\tag{数字}$$`|
|上大括号|`\overbrace{算式}`|$\overbrace{a+b+c+d}^{2.0}$|`$\overbrace{a+b+c+d}^{2.0}$`|
|下大括号|`\underbrace{算式}`|$a+\underbrace{b+c}_{1.0}+d$|`$a+\underbrace{b+c}_{1.0}+d$`|
|文字字体|`\mathrm`|$\mbox{更改后：}\mathrm{1Aa2Bb} \ \mbox{原：}{1Aa2Bb}$|`$\mbox{更改后：}\mathrm{1Aa2Bb} \ \mbox{原：}{1Aa2Bb}$`|
|上位符号|`\stacrel{上位符号}{基位符号}`|$\vec{x}\stackrel{\mathrm{def}}{=}{x_1,\dots,x_n}$|`$\vec{x}\stackrel{\mathrm{def}}{=}{x_1,\dots,x_n}$`|

## 占位符

| 说明 | 语法 | 用例 |用例源码|
| ---- | ---- | ---- | ---- |
| 换行 | `\\` | $x\\y$ |`$x\\y$`|
| 两个quad空格 | `\qquad` |$x \qquad y$|`$x \qquad y$`|
| quad空格 | `\quad` |$x \quad y$|`$x \quad y$`|
| 大空格 | `\` |$x \ y$|`$x \ y$`|
| 中空格 | `\:` |$x : y$|`$x : y$`|
| 小空格 | `\,` |$x , y$|`$x , y$`|
| 紧凑 | `\!` |$x ! y$|`$x ! y$`|

## 定界符与组合

| 说明       | 语法                                                  | 用例                                                         |用例源码|
| ---------- | ----------------------------------------------------- | ------------------------------------------------------------ |-------- |
| 括号       | `（）\big(\big) \Big(\Big) \bigg(\bigg) \Bigg(\Bigg)` |$（1）\big(2\big) \Big(3\Big) \bigg(4\bigg) \Bigg(5\Bigg)$ |`$（1）\big(2\big) \Big(3\Big) \bigg(4\bigg) \Bigg(5\Bigg)$` |
| 中括号     | `[]`                                                  |$[x+y]$                                                     |`$[x+y]$`                                                     |
| 大括号     | `\{ \}`                                               |$\{x+y\}$                                                 |`$\{x+y\}$`                                                 |
| 自适应括号 | `\left \right`                                        |$\left(x\right)    \left(x\{yz\}\right)$                   |`$\left(x\right)    \left(x\{yz\}\right)$`                   |
| 组合公式   | `{上位公式 \choose 下位公式}`                         |${n+1 \choose k}={n \choose k}+{n \choose k-1}$           |`${n+1 \choose k}={n \choose k}+{n \choose k-1}$`           |
| 组合公式   | `{上位公式 \atop 下位公式}`                           |$\sum_{k_0,k_1,\ldots>0 \atop k_0+k_1+\cdots=n}A_{k_0}A_{k_1}\cdots$|`$\sum_{k_0,k_1,\ldots>0 \atop k_0+k_1+\cdots=n}A_{k_0}A_{k_1}\cdots$`|
|            |                                                       |                                                              |                                                             |

## 四则运算

| 说明       | 语法                  | 用例                  |用例源码|
| ---------- | --------------------- | --------------------- |------ |
| 加法运算   | `+`                   |$x+y=z$            |`$x+y=z$`            |
| 减法运算   | `-`                   |$x-y=z$            |`$x-y=z$`            |
| 加减运算   | `\pm`                 |$x \pm y=z$        |`$x \pm y=z$`        |
| 减加运算   | `\mp`                 |$x \mp y=z$        |`$x \mp y=z$`        |
| 乘法运算   | `\times`              |$x \times y=z$     |`$x \times y=z$`     |
| 点乘运算   | `\cdot`               |$x \cdot y=z$      |`$x \cdot y=z$`      |
| 星乘运算   | `\ast`                |$x \ast y=z$       |`$x \ast y=z$`       |
| 除法运算   | `\div`                |$x \div y=z$       |`$x \div y=z$`       |
| 斜法运算   | `/`                   |$x/y=z$            |`$x/y=z$`            |
| 分式表示   | `\frac{分子}{分母}`   |$\frac{x+y}{y+z}$  |`$\frac{x+y}{y+z}$`  |
| 分式表示   | `{分子} \voer {分母}` |${x+y} \over {y+z}$|`${x+y} \over {y+z}$`|
| 绝对值表示 | `||`                  |$|x+y|$             |`$|x+y|$`             |

## 高级运算

| 说明         | 语法                          | 用例                                                        |用例源码|
| ------------ | ----------------------------- | ------------------------------------------------------------ |------------ |
| 平均数运算   | `\overline{算式}`             |$\overline{xyz}$                                          |`$\overline{xyz}$`                                          |
| 开二次方运算 | `\sqrt`                       |$\sqrt x$                                                 |`$\sqrt x$`                                                 |
| 开方运算     | `\sqrt[开方数]{被开方数}`     |$\sqrt[3]{x+y}$                                           |`$\sqrt[3]{x+y}$`                                           |
| 对数运算     | `\log`                        |$\log_2(x)$                                                |`$\log_2(x)$`                                                |
| 对数运算     | `\ln`                         |$\ln15$                                                   |`$\ln15$`                                                   |
| 对数运算     | `lg`                          |$\lg2$                                                      |`$\lg2$`                                                      |
| 极限运算     | `\lim`                        |$\lim^{x \to \infty}_{y \to 0}{\frac{x}{y}}$              |`$\lim^{x \to \infty}_{y \to 0}{\frac{x}{y}}$`              |
| 极限运算     | `\displaystyle \lim`          |$\displaystyle \lim^{x \to \infty}_{y \to 0}{\frac{x}{y}}$|`$\displaystyle \lim^{x \to \infty}_{y \to 0}{\frac{x}{y}}$`|
| 求和运算     | `\sum`                        |$\sum^{x \to \infty}_{y \to 0}{\frac{x}{y}}$              |`$\sum^{x \to \infty}_{y \to 0}{\frac{x}{y}}$`              |
| 求和运算     | `\displaystyle \sum`          |$\displaystyle \sum^{x \to \infty}_{y \to 0}{\frac{x}{y}}$|`$\displaystyle \sum^{x \to \infty}_{y \to 0}{\frac{x}{y}}$`|
| 积分运算     | `\int`                        |$\int^{\infty}_{0}{xdx}$                                  |`$\int^{\infty}_{0}{xdx}$`                                  |
| 积分运算     | `\displaystyle \int`          |$\displaystyle \int^{\infty}_{0}{xdx}$                    |`$\displaystyle \int^{\infty}_{0}{xdx}$`                    |
| 微分运算     | `\partial`                    |$\frac{\partial x}{\partial y}$                           |`$\frac{\partial x}{\partial y}$`                           |
| 矩阵表示     | `\begin{matrix} \end{matrix}` |$\left[ \begin{matrix} 1 &2 &\cdots &4\\5 &6 &\cdots &8\\vdots &\vdots &\ddots &\vdots\\13 &14 &\cdots &16\end{matrix} \right]$|`$\left[ \begin{matrix} 1 &2 &\cdots &4\\5 &6 &\cdots &8\\vdots &\vdots &\ddots &\vdots\\13 &14 &\cdots &16\end{matrix} \right]$`|

**矩阵补充：**

> 起始标记`\begin{matrix}`，结束标记`\end{matrix}`

> 每一行末尾标记`\\\`，行间元素之间以`&`分隔.

> 矩阵边框：
>
> - 在起始、结束标记处用下列词替换 `matrix`
> - `pmatrix` ：小括号边框
> - `bmatrix` ：中括号边框
> - `Bmatrix` ：大括号边框
> - `vmatrix` ：单竖线边框
> - `Vmatrix` ：双竖线边框

**阵列**：

> - 使用`array`替换 `matrix`
> - 对齐方式(类似于设置表头属性)：在`array`后以{}统一声明
    >

- 左对齐：`l`      是=>L

> - 居中：`e`
    >

- 右对齐：`r`

> - 垂直线：声明对其方式时，插入`|`建立竖线
> - 水平线：`\hline`

> 示例：$\begin{array}{c|lll}
> {↓}&{a}&{b}&{c}\\
> \hline
> {R_1}&{c}&{b}&{a}\\
> {R_2}&{b}&{c}&{c}\\
> \end{array}$
>
> ```
>$\begin{array}{c|lll}
> {↓}&{a}&{b}&{c}\\
> \hline
> {R_1}&{c}&{b}&{a}\\
> {R_2}&{b}&{c}&{c}\\
> \end{array}$
> ```

**方程组：**

> 起始需要`cases`替换 `matrix`，结束处以`{cases}`声明

> 示例：$\begin{cases}
> a_1x+b_1y+c_1z=d_1\\
> a_2x+b_2y+c_2z=d_2\\
> a_3x+b_3y+c_3z=d_3\\
> \end{cases}
> $
>
> ```
>$\begin{cases}
> a_1x+b_1y+c_1z=d_1\\
> a_2x+b_2y+c_2z=d_2\\
> a_3x+b_3y+c_3z=d_3\\
> \end{cases}
>$
> ```

## 逻辑运算

| 说明           | 语法       | 用例               |用例源码|
| -------------- | ---------- | ------------------ |------------- |
| 等于运算       | `=`        |$x+y=z$         |`$x+y=z$`         |
| 大于运算       | `>`        |$x+y>z$         |`$x+y>z$`         |
| 小于运算       | `<`        |$x+y<z$         |`$x+y<z$`         |
| 大于等于运算   | `\geq`     |$x+y \geq z$    |`$x+y \geq z$`    |
| 小于等于运算   | `\leq`     |$x+y \leq z$    |`$x+y \leq z$`    |
| 不等于运算     | `\neq`     |$x+y \neq z$    |`$x+y \neq z$`    |
| 不大于等于运算 | `\ngeq`    |$x+y \ngeq z$   |`$x+y \ngeq z$`   |
| 不大于等于运算 | `\not\geq` |$x+y \not\geq z$|`$x+y \not\geq z$`|
| 不小于等于运算 | `\nleq`    |$x+y \nleq z$   |`$x+y \nleq z$`   |
| 不小于等于运算 | `\not\leq` |$x+y \not\leq z$|`$x+y \not\leq z$`|
| 约等于运算     | `\approx`  |$x+y \approx z$ |`$x+y \approx z$` |
| 恒定等于运算   | `\equiv`   |$x+y \equiv z$  |`$x+y \equiv z$`  |

## 集合运算

| 说明         | 语法          | 用例                |用例源码|
| ------------ | ------------- | ------------------- |------------- |
| 属于运算     | `\in`         |$x \in y$        |`$x \in y$`        |
| 不属于运算   | `\notin`      |$x \notin y$     |`$x \notin y$`     |
| 不属于运算   | `\not\in`     |$x \not\in y$    |`$x \not\in y$`    |
| 子集运算     | `\subset`     |$x \subset y$    |`$x \subset y$`    |
| 子集运算     | `\supset`     |$x \supset y$    |`$x \supset y$`    |
| 真子集运算   | `\subseteq`   |$x \subseteq y$  |`$x \subseteq y$`  |
| 非真子集运算 | `\subsetneq`  |$x \subsetneq y$ |`$x \subsetneq y$` |
| 真子集运算   | `\supseteq`   |$x \supseteq y$  |`$x \supseteq y$`  |
| 非真子集运算 | `\supsetneq`  |$x \supsetneq y$ |`$x \supsetneq y$` |
| 非子集运算   | `\not\subset` |$x \not\subset y$|`$x \not\subset y$`|
| 非子集运算   | `\not\supset` |$x \not\supset y$|`$x \not\supset y$`|
| 并集运算     | `\cup`        |$x \cup y$       |`$x \cup y$`       |
| 交集运算     | `\cap`        |$x \cap y$       |`$x \cap y$`       |
| 差集运算     | `\setminus`   |$x \setminus y$  |`$x \setminus y$`  |
| 同或运算     | `\bigodot`    |$x \bigodot y$   |`$x \bigodot y$`   |
| 同与运算     | `\bigotimes`  |$x \bigotimes y$ |`$x \bigotimes y$` |
| 实数集合     | `\mathbb{R}`  |$\mathbb{R}$     |`$\mathbb{R}$`     |
| 自然数集合   | `\mathbb{Z}`  |$\mathbb{Z}$     |`$\mathbb{Z}$`     |
| 空集         | `\emptyset`   |$\emptyset$      |`$\emptyset$`      |

## 数学符号

| 说明             | 语法           | 用例                               |用例源码|
| ---------------- | -------------- | ---------------------------------- |------------------|
| 无穷             | `\infty`       |$\infty$                        |`$\infty$`                        |
| 虚数             | `\imath`       |$\imath$                        |`$\imath$`                        |
| 虚数             | `\jmath`       |$\jmath$                        |`$\jmath$`                        |
| 数学符号         | `\hat{a}`      |$\hat{a}$                       |`$\hat{a}$`                       |
| 数学符号         | `\check{a}`    |$\check{a}$                     |`$\check{a}$`                     |
| 数学符号         | `\breve{a}`    |$\breve{a}$                     |`$\breve{a}$`                     |
| 数学符号         | `\tilde{a}`    |$\tilde{a}$                     |`$\tilde{a}$`                     |
| 数学符号         | `\bar{a}`      |$\bar{a}$                       |`$\bar{a}$`                       |
| 矢量符号         | `\vec{a}`      |$\vec{a}$                       |`$\vec{a}$`                       |
| 矢量符号 | `\overrightarrow` |$\overrightarrow{a}$ |`$\overrightarrow{a}$` |
| 数学符号         | `\acute{a}`    |$\acute{a}$                     |`$\acute{a}$`                     |
| 数学符号         | `\grave{a}`    |$\grave{a}$                     |`$\grave{a}$`                     |
| 数学符号         | `\mathring{a}` |$\mathring{a}$                  |`$\mathring{a}$`                  |
| 一阶导数符号     | `\dot{a}`      |$\dot{a}$                       |`$\dot{a}$`                       |
| 二阶导数符号     | `\ddot{a}`     |$\ddot{a}$                      |`$\ddot{a}$`                      |
| 上箭头           | `\uparrow`     |$\uparrow$                      |`$\uparrow$`                      |
| 上箭头           | `\Uparrow`     |$\Uparrow$                      |`$\Uparrow$`                      |
| 下箭头           | `\downarrow`   |$\downarrow$                    |`$\downarrow$`                    |
| 下箭头           | `\Downarrow`   |$\Downarrow$                    |`$\Downarrow$`                    |
| 左箭头           | `\leftarrow`   |$\leftarrow$                    |`$\leftarrow$`                    |
| 左箭头 | `\longleftarrow` | $\longleftarrow$                 |`$\longleftarrow$` |
| 左箭头           | `\Leftarrow`   |$\Leftarrow$                    |`$\Leftarrow$`                    |
| 左箭头 | `\xleftarrow{}` |$\xleftarrow{x-1}$ |`$\xleftarrow{x-1}$` |
| 右箭头           | `\rightarrow`  |$\rightarrow$                   |`$\rightarrow$`                   |
| 右箭头           | `\Rightarrow`  |$\Rightarrow$                   |`$\Rightarrow$`                   |
| 右箭头 | `\longrightarrow` |$\longrightarrow$ |`$\longrightarrow$` |
| 右箭头 | `\xrightarrow{}` |$\xrightarrow{x-1}$ |`$\xrightarrow{x-1}$` |
| 右箭头 | `\xrightarrow[]{}` |$\xrightarrow[y-1]{x-1}$ |`$\xrightarrow[y-1]{x-1}$` |
| 底端对齐的省略号 | `\ldots`       |$1,2,\ldots,n$                  |`$1,2,\ldots,n$`                  |
| 中线对齐的省略号 | `\cdots`       |$x_1^2 + x_2^2 + \cdots + x_n^2$|`$x_1^2 + x_2^2 + \cdots + x_n^2$`|
| 竖直对齐的省略号 | `\vdots`       |$\vdots$                        |`$\vdots$`                        |
| 斜对齐的省略号   | `\ddots`       |$\ddots$                        |`$\ddots$`                        |
| 存在量词（若干） | `\exists`      |$\exists$                       |`$\exists$`                       |
| 全称量词（任意） | `\forall` |$\forall$ |`$\forall$` |
| 水平箭头 | `\harr` |$\harr$ |`$\harr$` |

## 三角函数

| 说明 | 语法   | 用例     |用例源码|
| ---- | ------ | -------- |----|
| sin  | `\sin` |$\sin$|`$\sin$`|
| cos  | `\cos` |$\cos$  |`$\cos$`  |
| tan  | `\tan` |$\tan$  |`$\tan$`  |

## 平面几何

| 说明     | 语法        | 用例        | 用例源码      |
| -------- | ----------- | ----------- | ------------- |
| 三角     | `\triangle` | $\triangle$ | `$\triangle$` |
| 垂直符号 | `\perp`     | $\perp$     | `$\perp$`     |
| 角       | `\angle`    | $\angle$    | `$\angle$`    |

## 希腊字母

| 字母       | 实现       | 字母       | 实现       |
| ---------- | ---------- | ---------- | ---------- |
| $\Alpha$   | `\Alpha`   | $\alpha$   | `\alpha`   |
| $\Beta$    | `\Beta`    | $\beta$    | `\beta`    |
| $\Gamma$   | `\Gamma`   | $\gamma$   | `\gamma`   |
| $\Delta$   | `\Delta`   | $\delta$   | `\delta`   |
| $\Epsilon$ | `\Epsilon` | $\epsilon$ | `\epsilon` |
| $\Zeta$    | `\Zeta`    | $\zeta$    | `\zeta`    |
| $\Eta$     | `\Eta`     | $\eta$     | `\eta`     |
| $\Theta$   | `\Theta`   | $\theta$   | `\theta`   |
| $\Iota$    | `\Iota`    | $\iota$    | `\iota`    |
| $\Kappa$   | `\Kappa`   | $\kappa$   | `\kappa`   |
| $\Lambda$  | `\Lambda`  | $\lambda$  | `\lambda`  |
| $\Mu$      | `\\Mu`     | $\mu$      | `\mu`      |
| $\Nu$      | `\Nu`      | $\nu$      | `\nu`      |
| $\Xi$      | `\Xi`      | $\xi$      | `\xi`      |
| $\Omicron$ | `\Omicron` | $\omicron$ | `\omicron` |
| $\Pi$      | `\Pi`      | $\pi$      | `\pi`      |
| $\Rho$     | `\Rho`     | $\rho$     | `\rho`     |
| $\Sigma$   | `\Sigma`   | $\sigma$   | `\sigma`   |
| $\Tau$     | `\Tau`     | $\tau$     | `\tau`     |
| $\Upsilon$ | `\Upsilon` | $\upsilon$ | `\upsilon` |
| $\Phi$     | `\Phi`     | $\phi$     | `\phi`     |
| $\Chi$     | `\Chi`     | $\chi$     | `\chi`     |
| $\Psi$     | `\Psi`     | $\psi$     | `\psi`     |
| $\Omega$   | `\Omega`   | $\omega$   | `\omega`   |
| $\varphi$  | `\varphi`  |            |            |

