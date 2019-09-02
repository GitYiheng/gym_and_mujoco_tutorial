# SVM

The **Support Vector Machine (SVM)** is a linear classifier that can be viewed as an extension of the **Perceptron** developed by Rosenblatt in 1958. The Perceptron guaranteed that you find **a** hyperplane if it exists. The SVM finds the **maximum margin** separating hyperplane.

*Setting*: We define a linear classifier: <a href="https://www.codecogs.com/eqnedit.php?latex=h(\mathbf{x})&space;=&space;\text{sign}(\mathbf{w}^{\top}&space;\mathbf{x}&space;&plus;&space;b)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?h(\mathbf{x})&space;=&space;\text{sign}(\mathbf{w}^{\top}&space;\mathbf{x}&space;&plus;&space;b)" title="h(\mathbf{x}) = \text{sign}(\mathbf{w}^{\top} \mathbf{x} + b)" /></a> and we assume a binary classification setting with labels <a href="https://www.codecogs.com/eqnedit.php?latex=\{&space;&plus;1,&space;-1&space;\}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\{&space;&plus;1,&space;-1&space;\}" title="\{ +1, -1 \}" /></a>.

Typically, if a data set is linearly separable, there are infinitely many separating hyperplanes. A natural question to ask is:

**Question: What is the best separating hyperplane?**

**SVM Answer: The one that maximizes the distance to the closest data points from both classes. We say it is the hyperplane with maximum margin.**

## Margin

We already saw the definition of a *margin* in the context of the *Perceptron*. A hyperplane is defined through <a href="https://www.codecogs.com/eqnedit.php?latex=\mathbf{w}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathbf{w}" title="\mathbf{w}" /></a>, <a href="https://www.codecogs.com/eqnedit.php?latex=b" target="_blank"><img src="https://latex.codecogs.com/gif.latex?b" title="b" /></a> as a set of points such that <a href="https://www.codecogs.com/eqnedit.php?latex=\mathcal{H}&space;=&space;\{&space;\mathbf{x}&space;\vert&space;\mathbf{w}^{\top}&space;\mathbf{x}&space;&plus;&space;b&space;=&space;0&space;\}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathcal{H}&space;=&space;\{&space;\mathbf{x}&space;\vert&space;\mathbf{w}^{\top}&space;\mathbf{x}&space;&plus;&space;b&space;=&space;0&space;\}" title="\mathcal{H} = \{ \mathbf{x} \vert \mathbf{w}^{\top} \mathbf{x} + b = 0 \}" /></a>. Let the margin <a href="https://www.codecogs.com/eqnedit.php?latex=\gamma" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\gamma" title="\gamma" /></a> be defined as the distance from the hyperplane to the closest point across both classes.

**What is the distance of a point <a href="https://www.codecogs.com/eqnedit.php?latex=\mathbf{x}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathbf{x}" title="\mathbf{x}" /></a> to the hyperplane <a href="https://www.codecogs.com/eqnedit.php?latex=\mathcal{H}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathcal{H}" title="\mathcal{H}" /></a>?**

Consider some point <a href="https://www.codecogs.com/eqnedit.php?latex=\mathbf{x}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathbf{x}" title="\mathbf{x}" /></a>. Let <a href="https://www.codecogs.com/eqnedit.php?latex=\mathbf{d}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathbf{d}" title="\mathbf{d}" /></a> be the vector from <a href="https://www.codecogs.com/eqnedit.php?latex=\mathcal{H}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathcal{H}" title="\mathcal{H}" /></a> to <a href="https://www.codecogs.com/eqnedit.php?latex=\mathbf{x}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathbf{x}" title="\mathbf{x}" /></a> of minimum length. Let <a href="https://www.codecogs.com/eqnedit.php?latex=\mathbf{x}^P" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathbf{x}^P" title="\mathbf{x}^P" /></a> be the projection of <a href="https://www.codecogs.com/eqnedit.php?latex=\mathbf{x}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathbf{x}" title="\mathbf{x}" /></a> onto <a href="https://www.codecogs.com/eqnedit.php?latex=\mathcal{H}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathcal{H}" title="\mathcal{H}" /></a>. It follows that:

<a href="https://www.codecogs.com/eqnedit.php?latex=\mathbf{x}^P&space;=&space;\mathbf{x}&space;-&space;\mathbf{d}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathbf{x}^P&space;=&space;\mathbf{x}&space;-&space;\mathbf{d}" title="\mathbf{x}^P = \mathbf{x} - \mathbf{d}" /></a>.

<a href="https://www.codecogs.com/eqnedit.php?latex=\mathbf{d}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathbf{d}" title="\mathbf{d}" /></a> is parallel to <a href="https://www.codecogs.com/eqnedit.php?latex=\mathbf{w}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathbf{w}" title="\mathbf{w}" /></a>, so <a href="https://www.codecogs.com/eqnedit.php?latex=\mathbf{d}&space;=&space;\alpha&space;\mathbf{w}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathbf{d}&space;=&space;\alpha&space;\mathbf{w}" title="\mathbf{d} = \alpha \mathbf{w}" /></a> for some <a href="https://www.codecogs.com/eqnedit.php?latex=\alpha&space;\in&space;\mathbb{R}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\alpha&space;\in&space;\mathbb{R}" title="\alpha \in \mathbb{R}" /></a>.

<a href="https://www.codecogs.com/eqnedit.php?latex=\mathbf{x}^P&space;\in&space;\mathcal{H}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathbf{x}^P&space;\in&space;\mathcal{H}" title="\mathbf{x}^P \in \mathcal{H}" /></a> which implies <a href="https://www.codecogs.com/eqnedit.php?latex=\mathbf{w}^{\top}&space;\mathbf{x}^P&space;&plus;&space;b&space;=&space;0" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathbf{w}^{\top}&space;\mathbf{x}^P&space;&plus;&space;b&space;=&space;0" title="\mathbf{w}^{\top} \mathbf{x}^P + b = 0" /></a>

therefore <a href="https://www.codecogs.com/eqnedit.php?latex=\mathbf{w}^{\top}&space;\mathbf{x}^P&space;&plus;&space;b&space;=&space;\mathbf{w}^{\top}&space;(\mathbf{x}&space;-&space;\mathbf{d})&space;&plus;&space;b&space;=&space;\mathbf{w}^{\top}&space;(\mathbf{x}&space;-&space;\alpha&space;\mathbf{w})&space;&plus;&space;b&space;=&space;0" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathbf{w}^{\top}&space;\mathbf{x}^P&space;&plus;&space;b&space;=&space;\mathbf{w}^{\top}&space;(\mathbf{x}&space;-&space;\mathbf{d})&space;&plus;&space;b&space;=&space;\mathbf{w}^{\top}&space;(\mathbf{x}&space;-&space;\alpha&space;\mathbf{w})&space;&plus;&space;b&space;=&space;0" title="\mathbf{w}^{\top} \mathbf{x}^P + b = \mathbf{w}^{\top} (\mathbf{x} - \mathbf{d}) + b = \mathbf{w}^{\top} (\mathbf{x} - \alpha \mathbf{w}) + b = 0" /></a>

which implies <a href="https://www.codecogs.com/eqnedit.php?latex=\alpha&space;=&space;\frac{\mathbf{w}^{\top}&space;\mathbf{x}&space;&plus;&space;b}{\mathbf{w}^{\top}&space;\mathbf{w}}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\alpha&space;=&space;\frac{\mathbf{w}^{\top}&space;\mathbf{x}&space;&plus;&space;b}{\mathbf{w}^{\top}&space;\mathbf{w}}" title="\alpha = \frac{\mathbf{w}^{\top} \mathbf{x} + b}{\mathbf{w}^{\top} \mathbf{w}}" /></a>

The length of <a href="https://www.codecogs.com/eqnedit.php?latex=\mathbf{d}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathbf{d}" title="\mathbf{d}" /></a>:

<a href="https://www.codecogs.com/eqnedit.php?latex=\|&space;\mathbf{d}&space;\|_2&space;=&space;\sqrt{\mathbf{d}^{\top}&space;\mathbf{d}}&space;=&space;\sqrt{\alpha^2&space;\mathbf{w}^{\top}&space;\mathbf{w}}&space;=&space;\frac{\vert&space;\mathbf{w}^{\top}&space;\mathbf{x}&space;&plus;&space;b&space;\vert}{\sqrt{\mathbf{w}^{\top}&space;\mathbf{w}}}&space;=&space;\frac{\vert&space;\mathbf{w}^{\top}&space;\mathbf{x}&space;&plus;&space;b&space;\vert}{\|&space;\mathbf{w}&space;\|_2}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\|&space;\mathbf{d}&space;\|_2&space;=&space;\sqrt{\mathbf{d}^{\top}&space;\mathbf{d}}&space;=&space;\sqrt{\alpha^2&space;\mathbf{w}^{\top}&space;\mathbf{w}}&space;=&space;\frac{\vert&space;\mathbf{w}^{\top}&space;\mathbf{x}&space;&plus;&space;b&space;\vert}{\sqrt{\mathbf{w}^{\top}&space;\mathbf{w}}}&space;=&space;\frac{\vert&space;\mathbf{w}^{\top}&space;\mathbf{x}&space;&plus;&space;b&space;\vert}{\|&space;\mathbf{w}&space;\|_2}" title="\| \mathbf{d} \|_2 = \sqrt{\mathbf{d}^{\top} \mathbf{d}} = \sqrt{\alpha^2 \mathbf{w}^{\top} \mathbf{w}} = \frac{\vert \mathbf{w}^{\top} \mathbf{x} + b \vert}{\sqrt{\mathbf{w}^{\top} \mathbf{w}}} = \frac{\vert \mathbf{w}^{\top} \mathbf{x} + b \vert}{\| \mathbf{w} \|_2}" /></a>

Margin of <a href="https://www.codecogs.com/eqnedit.php?latex=\mathcal{H}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathcal{H}" title="\mathcal{H}" /></a> with respect to <a href="https://www.codecogs.com/eqnedit.php?latex=D" target="_blank"><img src="https://latex.codecogs.com/gif.latex?D" title="D" /></a>: <a href="https://www.codecogs.com/eqnedit.php?latex=\gamma&space;(\mathbf{w},&space;b)&space;=&space;\operatorname*{argmin}_{\mathbf{x}&space;\in&space;D}&space;\frac{\vert&space;\mathbf{w}^{\top}&space;\mathbf{x}&space;&plus;&space;b&space;\vert}{\|&space;\mathbf{w}&space;\|_2}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\gamma&space;(\mathbf{w},&space;b)&space;=&space;\operatorname*{argmin}_{\mathbf{x}&space;\in&space;D}&space;\frac{\vert&space;\mathbf{w}^{\top}&space;\mathbf{x}&space;&plus;&space;b&space;\vert}{\|&space;\mathbf{w}&space;\|_2}" title="\gamma (\mathbf{w}, b) = \operatorname*{argmin}_{\mathbf{x} \in D} \frac{\vert \mathbf{w}^{\top} \mathbf{x} + b \vert}{\| \mathbf{w} \|_2}" /></a>

By definition, the margin and hyperplane are scale invariant: <a href="https://www.codecogs.com/eqnedit.php?latex=\gamma&space;(\beta&space;\mathbf{w},&space;\beta&space;b)&space;=&space;\gamma&space;(\mathbf{w},&space;b),&space;\enspace&space;\forall&space;\beta&space;\neq&space;0" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\gamma&space;(\beta&space;\mathbf{w},&space;\beta&space;b)&space;=&space;\gamma&space;(\mathbf{w},&space;b),&space;\enspace&space;\forall&space;\beta&space;\neq&space;0" title="\gamma (\beta \mathbf{w}, \beta b) = \gamma (\mathbf{w}, b), \enspace \forall \beta \neq 0" /></a>

Note that if the hyperplane is such that <a href="https://www.codecogs.com/eqnedit.php?latex=\gamma" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\gamma" title="\gamma" /></a> is maximized, it must lie right in the middle of the two classes. In other words, <a href="https://www.codecogs.com/eqnedit.php?latex=\gamma" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\gamma" title="\gamma" /></a> must be the distance to the closest point within *both* classes. (If not, you could move the hyperplane towards data points of the class that is further away and increase <a href="https://www.codecogs.com/eqnedit.php?latex=\gamma" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\gamma" title="\gamma" /></a>, which contradicts that <a href="https://www.codecogs.com/eqnedit.php?latex=\gamma" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\gamma" title="\gamma" /></a> is maximized.)

## Max Margin Classifier

We can formulate our search for the maximum margin separating hyperplane as a constrained optimization problem. The objective is to maximize the margin under the constraints that all data points must lie on the correct side of the hyperplane:

<a href="https://www.codecogs.com/eqnedit.php?latex=\underbrace{\max_{\mathbf{w},&space;b}&space;\gamma&space;(\mathbf{w},&space;b)}_{\text{maximize&space;margin}}&space;\text{&space;such&space;that&space;}&space;\underbrace{\forall&space;i&space;\enspace&space;y_i&space;(\mathbf{w}^{\top}&space;x_i&space;&plus;&space;b)&space;\geq&space;0}_{\text{separating&space;hyperplane}}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\underbrace{\max_{\mathbf{w},&space;b}&space;\gamma&space;(\mathbf{w},&space;b)}_{\text{maximize&space;margin}}&space;\text{&space;such&space;that&space;}&space;\underbrace{\forall&space;i&space;\enspace&space;y_i&space;(\mathbf{w}^{\top}&space;x_i&space;&plus;&space;b)&space;\geq&space;0}_{\text{separating&space;hyperplane}}" title="\underbrace{\max_{\mathbf{w}, b} \gamma (\mathbf{w}, b)}_{\text{maximize margin}} \text{ such that } \underbrace{\forall i \enspace y_i (\mathbf{w}^{\top} x_i + b) \geq 0}_{\text{separating hyperplane}}" /></a>

If we plug in the definition of <a href="https://www.codecogs.com/eqnedit.php?latex=\gamma" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\gamma" title="\gamma" /></a> we obtain:

Because the hyperplane is scale invariant, we can fix the scale of <a href="https://www.codecogs.com/eqnedit.php?latex=\mathbf{w}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathbf{w}" title="\mathbf{w}" /></a>, <a href="https://www.codecogs.com/eqnedit.php?latex=b" target="_blank"><img src="https://latex.codecogs.com/gif.latex?b" title="b" /></a> anyway we want. Let's be clever about it, and choose it such that

<a href="https://www.codecogs.com/eqnedit.php?latex=\min_{\mathbf{x}&space;\in&space;D}&space;\vert&space;\mathbf{w}^{\top}&space;\mathbf{x}&space;&plus;&space;b&space;\vert&space;=&space;1" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\min_{\mathbf{x}&space;\in&space;D}&space;\vert&space;\mathbf{w}^{\top}&space;\mathbf{x}&space;&plus;&space;b&space;\vert&space;=&space;1" title="\min_{\mathbf{x} \in D} \vert \mathbf{w}^{\top} \mathbf{x} + b \vert = 1" /></a>

We can add this re-scaling as an equality constraint. Then our objective becomes:

<a href="https://www.codecogs.com/eqnedit.php?latex=\max_{\mathbf{w},&space;b}&space;\frac{1}{\|&space;\mathbf{w}&space;\|_2}&space;\cdot&space;1&space;=&space;\min_{\mathbf{w},&space;b}&space;\|&space;\mathbf{w}&space;\|_2&space;=&space;\min_{\mathbf{w},&space;b}&space;\mathbf{w}^{\top}&space;\mathbf{w}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\max_{\mathbf{w},&space;b}&space;\frac{1}{\|&space;\mathbf{w}&space;\|_2}&space;\cdot&space;1&space;=&space;\min_{\mathbf{w},&space;b}&space;\|&space;\mathbf{w}&space;\|_2&space;=&space;\min_{\mathbf{w},&space;b}&space;\mathbf{w}^{\top}&space;\mathbf{w}" title="\max_{\mathbf{w}, b} \frac{1}{\| \mathbf{w} \|_2} \cdot 1 = \min_{\mathbf{w}, b} \| \mathbf{w} \|_2 = \min_{\mathbf{w}, b} \mathbf{w}^{\top} \mathbf{w}" /></a>

(Where we made use of the fact <a href="https://www.codecogs.com/eqnedit.php?latex=f(z)&space;=&space;z^2" target="_blank"><img src="https://latex.codecogs.com/gif.latex?f(z)&space;=&space;z^2" title="f(z) = z^2" /></a> is a monotonically increasing function for <a href="https://www.codecogs.com/eqnedit.php?latex=z&space;\geq&space;0" target="_blank"><img src="https://latex.codecogs.com/gif.latex?z&space;\geq&space;0" title="z \geq 0" /></a> and <a href="https://www.codecogs.com/eqnedit.php?latex=\|&space;\mathbf{w}&space;\|&space;\geq&space;0" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\|&space;\mathbf{w}&space;\|&space;\geq&space;0" title="\| \mathbf{w} \| \geq 0" /></a>; i.e. the <a href="https://www.codecogs.com/eqnedit.php?latex=\mathbf{w}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathbf{w}" title="\mathbf{w}" /></a> that maximizes <a href="https://www.codecogs.com/eqnedit.php?latex=\|&space;\mathbf{w}&space;\|_2" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\|&space;\mathbf{w}&space;\|_2" title="\| \mathbf{w} \|_2" /></a> also maximizes <a href="https://www.codecogs.com/eqnedit.php?latex=\mathbf{w}^{\top}\mathbf{w}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathbf{w}^{\top}\mathbf{w}" title="\mathbf{w}^{\top}\mathbf{w}" /></a>.)

The new optimization problem becomes:

<a href="https://www.codecogs.com/eqnedit.php?latex=\min_{\mathbf{w},&space;b}&space;\mathbf{w}^{\top}&space;\mathbf{w}&space;\qquad\text{s.t.}&space;\begin{array}{ll}&space;\forall&space;i,&space;\enspace&space;y_i&space;(\mathbf{w}^{\top}&space;\mathbf{x}_i&space;&plus;&space;b)&space;\geq&space;0&space;\\&space;\min_{i}&space;\vert&space;\mathbf{w}^{\top}&space;\mathbf{x}_i&space;&plus;&space;b&space;\vert&space;=&space;1&space;\end{array}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\min_{\mathbf{w},&space;b}&space;\mathbf{w}^{\top}&space;\mathbf{w}&space;\qquad\text{s.t.}&space;\begin{array}{ll}&space;\forall&space;i,&space;\enspace&space;y_i&space;(\mathbf{w}^{\top}&space;\mathbf{x}_i&space;&plus;&space;b)&space;\geq&space;0&space;\\&space;\min_{i}&space;\vert&space;\mathbf{w}^{\top}&space;\mathbf{x}_i&space;&plus;&space;b&space;\vert&space;=&space;1&space;\end{array}" title="\min_{\mathbf{w}, b} \mathbf{w}^{\top} \mathbf{w} \qquad\text{s.t.} \begin{array}{ll} \forall i, \enspace y_i (\mathbf{w}^{\top} \mathbf{x}_i + b) \geq 0 \\ \min_{i} \vert \mathbf{w}^{\top} \mathbf{x}_i + b \vert = 1 \end{array}" /></a>

These constraints are still hard to deal with, however luckily we can show that (for the optimal solution) they are equivalent to a much simpler formulation. (Makes sure you know how to prove that the two sets of constraints are equivalent.)

<a href="https://www.codecogs.com/eqnedit.php?latex=\min_{\mathbf{w},&space;b}&space;\mathbf{w}^{\top}&space;\mathbf{w}&space;\qquad\text{s.t.}&space;\enspace&space;\forall&space;i,&space;\enspace&space;y_i&space;(\mathbf{w}^{\top}&space;\mathbf{x}_i&space;&plus;&space;b)&space;\geq&space;1" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\min_{\mathbf{w},&space;b}&space;\mathbf{w}^{\top}&space;\mathbf{w}&space;\qquad\text{s.t.}&space;\enspace&space;\forall&space;i,&space;\enspace&space;y_i&space;(\mathbf{w}^{\top}&space;\mathbf{x}_i&space;&plus;&space;b)&space;\geq&space;1" title="\min_{\mathbf{w}, b} \mathbf{w}^{\top} \mathbf{w} \qquad\text{s.t.} \enspace \forall i, \enspace y_i (\mathbf{w}^{\top} \mathbf{x}_i + b) \geq 1" /></a>

This new formulation is a *quadratic optimization problem*. The objective is *quadratic* and the constraints are all *linear*. We can solve it efficiently with any QCQP (Quadratically Constrained Quadratic Program) solver. It has a unique solution wheneverr a separating hyperplane exists. It also has a nice interpretation: Find the simplest hyperplane (where simpler means smaller <a href="https://www.codecogs.com/eqnedit.php?latex=\mathbf{w}^{\top}&space;\mathbf{w}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathbf{w}^{\top}&space;\mathbf{w}" title="\mathbf{w}^{\top} \mathbf{w}" /></a>) such that all inputs lie at least 1 unit away from the hyperplane on the correct side.

### Support Vectors

For the optimal <a href="https://www.codecogs.com/eqnedit.php?latex=\mathbf{w}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathbf{w}" title="\mathbf{w}" /></a>, <a href="https://www.codecogs.com/eqnedit.php?latex=b" target="_blank"><img src="https://latex.codecogs.com/gif.latex?b" title="b" /></a> pair, some training points will have tight constraints, i.e.

<a href="https://www.codecogs.com/eqnedit.php?latex=y_i&space;(\mathbf{w}^{\top}&space;\mathbf{x}_i&space;&plus;&space;b)&space;=&space;1" target="_blank"><img src="https://latex.codecogs.com/gif.latex?y_i&space;(\mathbf{w}^{\top}&space;\mathbf{x}_i&space;&plus;&space;b)&space;=&space;1" title="y_i (\mathbf{w}^{\top} \mathbf{x}_i + b) = 1" /></a>

(This must be the case, because if for all training points we had a strict <a href="https://www.codecogs.com/eqnedit.php?latex=>" target="_blank"><img src="https://latex.codecogs.com/gif.latex?>" title=">" /></a> inequality, it would be possible to scale down both parameters <a href="https://www.codecogs.com/eqnedit.php?latex=\mathbf{w}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathbf{w}" title="\mathbf{w}" /></a>, <a href="https://www.codecogs.com/eqnedit.php?latex=b" target="_blank"><img src="https://latex.codecogs.com/gif.latex?b" title="b" /></a> until the constraints are tight and obtained an even lower objective value.) We refer to these training points as **support vectors**. Support vectors are special because they are the training points that define the maximum margin of the hyperplane to the data set and they therefore determine the shape of the hyperplane. If you were to move one of them and retrain the SVM, the resulting hyperplane would change. The opposite is the case for non-support vectors (provided you don't move them too much, or they would turn into support vectors themselves).

## SVM with Soft Constraints

If the data is low dimensional it is often the case that there is no separating hyperplane between the two classes.In this case, there is no solution to the optimization problems stated above. We can fix this by allowing the constraints to be violated ever so slight with the introduction of slack variables:

<a href="https://www.codecogs.com/eqnedit.php?latex=\begin{align*}&space;\min_{\mathbf{w},&space;b}&space;\mathbf{w}^{\top}&space;\mathbf{w}&space;&plus;&space;C&space;&&space;\sum_{i=1}^{n}&space;\xi_i&space;\\&space;\text{s.t.&space;}&space;\forall&space;i,&space;y_i&space;(\mathbf{w}^{\top}&space;\mathbf{x}_i&space;&plus;&space;b)&space;&&space;\geq&space;1&space;-&space;\xi_i&space;\\&space;\forall&space;i,&space;\xi_i&space;&&space;\geq&space;0&space;\end{align*}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\begin{align*}&space;\min_{\mathbf{w},&space;b}&space;\mathbf{w}^{\top}&space;\mathbf{w}&space;&plus;&space;C&space;&&space;\sum_{i=1}^{n}&space;\xi_i&space;\\&space;\text{s.t.&space;}&space;\forall&space;i,&space;y_i&space;(\mathbf{w}^{\top}&space;\mathbf{x}_i&space;&plus;&space;b)&space;&&space;\geq&space;1&space;-&space;\xi_i&space;\\&space;\forall&space;i,&space;\xi_i&space;&&space;\geq&space;0&space;\end{align*}" title="\begin{align*} \min_{\mathbf{w}, b} \mathbf{w}^{\top} \mathbf{w} + C & \sum_{i=1}^{n} \xi_i \\ \text{s.t. } \forall i, y_i (\mathbf{w}^{\top} \mathbf{x}_i + b) & \geq 1 - \xi_i \\ \forall i, \xi_i & \geq 0 \end{align*}" /></a>

The slack variable <a href="https://www.codecogs.com/eqnedit.php?latex=\xi_i" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\xi_i" title="\xi_i" /></a> allows the input <a href="https://www.codecogs.com/eqnedit.php?latex=\mathbf{x}_i" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathbf{x}_i" title="\mathbf{x}_i" /></a> to be closer to the hyperplane (or even be on the wrong side), but there is a penalty in the objective function for such "slack". If <a href="https://www.codecogs.com/eqnedit.php?latex=C" target="_blank"><img src="https://latex.codecogs.com/gif.latex?C" title="C" /></a> is very large, the SVM becomes very strict and tries to get all points to be on the right side of the hyperplane. If <a href="https://www.codecogs.com/eqnedit.php?latex=C" target="_blank"><img src="https://latex.codecogs.com/gif.latex?C" title="C" /></a> is very small, the SVM becomes very loose and may "sacrifice" some points to obtain a simpler (i.e. lower <a href="https://www.codecogs.com/eqnedit.php?latex=\|&space;\mathbf{w}&space;\|_2^2" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\|&space;\mathbf{w}&space;\|_2^2" title="\| \mathbf{w} \|_2^2" /></a>) solution.

### Unconstrained Formulation:

Let us consider the value of <a href="https://www.codecogs.com/eqnedit.php?latex=\xi_i" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\xi_i" title="\xi_i" /></a> for the case of <a href="https://www.codecogs.com/eqnedit.php?latex=C&space;\neq&space;0" target="_blank"><img src="https://latex.codecogs.com/gif.latex?C&space;\neq&space;0" title="C \neq 0" /></a>. Because the objective will always try to minimize <a href="https://www.codecogs.com/eqnedit.php?latex=\xi_i" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\xi_i" title="\xi_i" /></a> as much as possible, the equation must hold as an *equality* and we have:

<a href="https://www.codecogs.com/eqnedit.php?latex=\xi_i&space;=&space;\left\{&space;\begin{array}{ll}&space;1&space;-&space;y_i&space;(\mathbf{w}^{\top}&space;\mathbf{x}_i&space;&plus;&space;b)&space;&&space;\text{if&space;}\enspace&space;y_i&space;(\mathbf{w}^{\top}&space;\mathbf{x}_i&space;&plus;&space;b)&space;<&space;1&space;\\&space;0&space;&&space;\text{if&space;}\enspace&space;y_i&space;(\mathbf{w}^{\top}&space;\mathbf{x}_i&space;&plus;&space;b)&space;\geq&space;1&space;\end{array}&space;\right." target="_blank"><img src="https://latex.codecogs.com/gif.latex?\xi_i&space;=&space;\left\{&space;\begin{array}{ll}&space;1&space;-&space;y_i&space;(\mathbf{w}^{\top}&space;\mathbf{x}_i&space;&plus;&space;b)&space;&&space;\text{if&space;}\enspace&space;y_i&space;(\mathbf{w}^{\top}&space;\mathbf{x}_i&space;&plus;&space;b)&space;<&space;1&space;\\&space;0&space;&&space;\text{if&space;}\enspace&space;y_i&space;(\mathbf{w}^{\top}&space;\mathbf{x}_i&space;&plus;&space;b)&space;\geq&space;1&space;\end{array}&space;\right." title="\xi_i = \left\{ \begin{array}{ll} 1 - y_i (\mathbf{w}^{\top} \mathbf{x}_i + b) & \text{if }\enspace y_i (\mathbf{w}^{\top} \mathbf{x}_i + b) < 1 \\ 0 & \text{if }\enspace y_i (\mathbf{w}^{\top} \mathbf{x}_i + b) \geq 1 \end{array} \right." /></a>

This is equivalent to the following closed form:

<a href="https://www.codecogs.com/eqnedit.php?latex=\xi_i&space;=&space;\max&space;(1&space;-&space;y_i&space;(\mathbf{w}^{\top}&space;\mathbf{x}_i&space;&plus;&space;b),&space;0)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\xi_i&space;=&space;\max&space;(1&space;-&space;y_i&space;(\mathbf{w}^{\top}&space;\mathbf{x}_i&space;&plus;&space;b),&space;0)" title="\xi_i = \max (1 - y_i (\mathbf{w}^{\top} \mathbf{x}_i + b), 0)" /></a>

If we plug this closed form into the objective of our SVM optimization problem, we obtain the following *unconstrained* version as loss function and regularizer:

<a href="https://www.codecogs.com/eqnedit.php?latex=\min_{\mathbf{w},&space;b}&space;\underbrace{\mathbf{w}^{\top}&space;\mathbf{w}}_{\ell_2\text{--regularizer}}&space;&plus;&space;C&space;\sum_{i=1}^{n}&space;\underbrace{\max&space;[1&space;-&space;y_i&space;(\mathbf{w}^{\top}&space;\mathbf{x}&space;&plus;&space;b),&space;0]}_{\text{hinge--loss}}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\min_{\mathbf{w},&space;b}&space;\underbrace{\mathbf{w}^{\top}&space;\mathbf{w}}_{\ell_2\text{--regularizer}}&space;&plus;&space;C&space;\sum_{i=1}^{n}&space;\underbrace{\max&space;[1&space;-&space;y_i&space;(\mathbf{w}^{\top}&space;\mathbf{x}&space;&plus;&space;b),&space;0]}_{\text{hinge--loss}}" title="\min_{\mathbf{w}, b} \underbrace{\mathbf{w}^{\top} \mathbf{w}}_{\ell_2\text{--regularizer}} + C \sum_{i=1}^{n} \underbrace{\max [1 - y_i (\mathbf{w}^{\top} \mathbf{x} + b), 0]}_{\text{hinge--loss}}" /></a>

This formulation allows us to optimize the SVM parameters <a href="https://www.codecogs.com/eqnedit.php?latex=(\mathbf{w},&space;b)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?(\mathbf{w},&space;b)" title="(\mathbf{w}, b)" /></a> just like logistic regression (e.g. through gradient descent). The only difference is that we have the **hinge--loss** instead of the **logistic loss**.