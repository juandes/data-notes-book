## Hashing Trick

Every now and then, when using linear methods such as Support Vector Machines \(SVM\), we could encounter the case where our dataset is not linearly separable, making it hard for the learner to learn a precise and optimal distinction between the labels of the dataset. For example, the next picture represents a dataset with data whose classes are not linearly separable, in other words, there is no a single line able to separate the dataset so that each side of the line is made of observations of the same class.

![](/assets/non_linearly_separable.png)

What do we do in such a case? An option is to apply what is called the "kernel trick". For starters, a kernel function is basically a mapping function that transforms a space into a higher versional version of it.  These functions are really useful because by transforming the feature space into a high dimensional one, the algorithm might find a line or hyperplane that separates the dataset.

The above picture is a two-dimensional space in which there is no line that can separate the data between the A points and B points. However, see how by transforming the space from two dimensions, into three, we find a hyperplane that separates the data.

![](/assets/Screen Shot 2018-01-29 at 18.09.52.png)

The "trick" part of the expression "kernel trick" comes from the fact that there is really no need of transforming the whole space into a high dimensional version of it. Instead, while solving an SVM, the algorithm only needs to calculate the inner product of the vectors in the feature space. For example, for a kernel function $$K$$, and input $$x$$ and $$y$$, $$K$$ will project these data points in a high dimensional space, and it is represented by the following equation:


$$
S(x,y)= \langle K(x), K(y) \rangle
$$




**NEXT**: Write an example in code  
**NEXT**: Write an example using math
**NEXT**: List several kernel functions

