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
\mathbf{x} = (x_1, x_2, ..., x_n), \mathbf{y} = (x_1, x_2, ..., x_n)
$$


##### Example

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

The Euclidean distance, also known as the $$L_2$$ distance is the "normal" straight line distance that is calculated by finding the length between two points in the space.


$$
d(\mathbf{x},\mathbf{y})= \sqrt{\sum_{i=1}^{n}(x_i - y_i)^2}
$$


where both $$\mathbf{x}$$ and $$\mathbf{y}$$ are vectors of the shape


$$
\mathbf{x} = (x_1, x_2, ..., x_n), \mathbf{y} = (x_1, x_2, ..., x_n)
$$


##### Example

For vectors $$\mathbf{x} = (1,13)$$ and $$\mathbf{y} = (2,9)$$, the Manhattan Distance is $$d(\mathbf{x},\mathbf{y})= \sqrt{(1-2)^2 + (13 - 9)^2} = 4.12 $$.

##### R Snippet

```
> x <- c(1,13)
> y <- c(2,9)
> dist(rbind(x,y), method = 'euclidean')
         x
y 4.123106
```

### Minkowski Distance

Minkowski Distance is a generalisation of the previous two distances discussed (Manhattan and Euclidean). It looks like this:

$$
(\sum_{i=1}^{n}|x_i-y_i|^p)^\frac{1}{p}
$$

where $$p$$ is typically $$1$$ or $$2$$. If used with the latest, the equation is the same as the Manhattan distance, with the former, it becomes the Euclidean distance, and both $$\mathbf{x}$$ and $$\mathbf{y}$$ are vectors of the shape





$$
\mathbf{x} = (x_1, x_2, ..., p_n), \mathbf{y} = (x_1, x_2, ..., x_n)
$$



### Cosine Similarity

The cosine similarity is a measure of similarity that quantifies the cosine of the angle between two vectors. If used in a positive-values space, the value will always be between 0 and 1, where 0 means dissimilarity and 1 means complete similarity. 

The equation is the following:

$$
cosine\_similarity = \cos(\theta) = \frac{\mathbf{X}\cdot{}\mathbf{Y}}{||\mathbf{X}||_2||\mathbf{Y}||_2} = \frac{\sum_{i=1}^{n}x_iy_i}{\sqrt{\sum_{i=1}^{n}X_i^2}\sqrt{\sum_{i=1}^{n}Y_i^2}}
$$

The upper part of the fraction, $${\mathbf{X}\cdot{}\mathbf{Y}}$$, is the dot product of both vectors, and the lower part is the product of the magnitude(also known as the length or Euclidean norm) of each vector. The next example 

##### Example
Soon :)

