## Similarity and Distance Measures

When clustering objects in unsupervised learning, one of the most important concepts is that of **similarity** and **distance** measure. The reason behind this is that to perform a good cluster, the model must know how similar or dissimilar the objects are from each other.

A similarity measure is usually based on a function, let's call it a similarity function, that estimate how alike how two objects are. Most similarities functions return a value between 0 and 1, where 0 means that both objects are completely different, while 1 means they are absolutely similar.

A distance measure \(also called **dissimilarity**\) is the opposite of the similarity measure. Instead of evaluating how similar two objects are, it computes how distant or different they are from one another. Normally, the values range from 0 to infinity, where 0 means complete similarity, and the greater the value, the more different they are.

Over the next couple of paragraphs, I will present some of the most used distance and similarity measures.

### Manhattan Distance

The Manhattan distance, also known as the Taxicab distance or $$ L_i$$ distance is a distance which is calculated by adding the absolute difference \(absolute value\) of their cartesian coordinates.


$$
d_1(\mathbf{x},\mathbf{y})= ||\mathbf{x} - \mathbf{y}||_1 = \sum_{i=1}^{n}|x_i - y_i|
$$


where both $$\mathbf{x}$$ and $$\mathbf{y}$$ are vectors of the shape


$$
\mathbf{x} = (p_1, p_2, ..., p_n), \mathbf{y} = (p_1, p_2, ..., p_n)
$$


##### Example:

For vectors $$\mathbf{x} = (1,13)$$ and $$\mathbf{y} = (2,9)$$, the Manhattan Distance is $$d_1(\mathbf{x},\mathbf{y})= |1-2| + |13 - 9| = 5 $$.

##### R Snippet

```
> x <- c(1,13)
> y <- c(2,9)
> dist(rbind(x,y), method = 'manhattan')
  x
y 5

```

### Euclidean Distance

Soon...

### Minkowski Distance

Soon...



