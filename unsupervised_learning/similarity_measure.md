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

Minkowski Distance is a generalisation of the previous two distances discussed \(Manhattan and Euclidean\). It looks like this:


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


The upper part of the fraction, $${\mathbf{X}\cdot{}\mathbf{Y}}$$, is the dot product of both vectors, and the lower part is the product of the magnitude\(also known as the length or Euclidean norm\) of each vector.

##### Example

Suppose we have two vectors $$x=(8,9,0,1,3,3)$$ and $$y=(10,9,2,11,3,4)$$.  
First, we need to calculate the dot product $$\mathbf{X}\cdot{}\mathbf{Y}$$.


$$
\mathbf{X}\cdot{}\mathbf{Y} = (8\times10)+(9\times9)+(0\times2)+(1\times11)+(3\times3)+(3\times4) = 193
$$


Then, we calculate $$||\mathbf{X}||_2$$ and $$||\mathbf{y}||_2$$:
$$
||\mathbf{X}||_2 = \sqrt{(8\times8)+(9\times9)+(0\times0)+(1\times1)+(3\times3)+(3\times3)}=12.80
$$


and  
$$
||\mathbf{Y}||_2 = \sqrt{(10\times10)+(9\times9)+(2\times2)+(11\times11)+(3\times3)+(4\times4)}=18.19
$$


Now that we have everything, we calculate the cosine similarity.


$$
\cos(x,y) = \frac{\mathbf{X}\cdot{}\mathbf{Y}}{||\mathbf{X}||_2||\mathbf{Y}||_2} = \frac{193}{12.80\times18.19}=0.82
$$


##### R Snippet of the problem

```
> x <- c(8,9,0,1,3,3)
> y <- c(10,9,2,11,3,4)
> dot <- x%*%y
> norm.x <- sqrt(sum(x^2))
> norm.y <- sqrt(sum(y^2))
> cosine <- (dot) / (norm.x*norm.y)
> print(as.numeric(cosine))
[1] 0.8283643
```

The cosine similarity is often used to determine how similar two texts are. The approach involves creating a bag of words with the frequency of each term in the documents. Then, each "row" of terms is converted to a vector. For example, suppose we have two documents **X **and **Y**, and **X **says _"friday is my favorite day" _and **Y** _"mondays is my least favorite day"_.  A bag of word would look like this:

| Doc. | friday | is | my | favorite | day | mondays | are | least |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| X | 1 | 1 | 1 | 1 | 1 | 0 | 0 | 0 |
| Y | 0 | 0 | 1 | 1 | 1 | 0 | 1 | 1 |

The vectorial representation would look like this:

$$x = (1,1,1,1,1,0,0,0)$$ and $$y = (0,0,1,1,1,0,1,1)$$.

