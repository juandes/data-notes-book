# Similarity and Distance Measures

When clustering objects in unsupervised learning, one of the most important concepts is that of **similarity** and **distance** measure. The reason behind this is that to perform a good cluster, the model must know how similar or dissimilar the objects are from each other.

A similarity measure is usually based on a function, let's call it a similarity function, that estimate how alike how two objects are. Most similarities functions return a value between 0 and 1, where 0 means that both objects are completely different, while 1 means they are absolutely similar.

A distance measure \(also called **dissimilarity**\) is the opposite of the similarity measure. Instead of evaluating how similar two objects are, it computes how distant or different they are from one another. Normally, the values range from 0 to infinity, where 0 means complete similarity, and the greater the value, the more different they are.

Over the next couple of paragraphs, I will present some of the most used distance and similarity measures.

## Manhattan Distance

The Manhattan distance, also known as the Taxicab distance or  distance is a distance which is calculated by adding the absolute difference \(absolute value\) of their cartesian coordinates.

where both  and  are vectors of the shape

### Example

For vectors  and , the Manhattan Distance is .

### R Snippet

```text
> x <- c(1,13)
> y <- c(2,9)
> dist(rbind(x,y), method = 'manhattan')
  x
y 5
```

## Euclidean Distance

The Euclidean distance, also known as the  distance is the "normal" straight line distance that is calculated by finding the length between two points in the space.

where both  and  are vectors of the shape

### Example

For vectors  and , the Manhattan Distance is .

### R Snippet

```text
> x <- c(1,13)
> y <- c(2,9)
> dist(rbind(x,y), method = 'euclidean')
         x
y 4.123106
```

## Minkowski Distance

Minkowski Distance is a generalisation of the previous two distances discussed \(Manhattan and Euclidean\). It looks like this:

where  is typically  or . If used with the latest, the equation is the same as the Manhattan distance, with the former, it becomes the Euclidean distance, and both  and  are vectors of the shape

## Cosine Similarity

The cosine similarity is a measure of similarity that quantifies the cosine of the angle between two vectors. If used in a positive-values space, the value will always be between 0 and 1, where 0 means dissimilarity and 1 means complete similarity.

The equation is the following:

The upper part of the fraction, , is the dot product of both vectors, and the lower part is the product of the magnitude\(also known as the length or Euclidean norm\) of each vector.

### Example

Suppose we have two vectors  and .  
First, we need to calculate the dot product .

Then, we calculate  and :

and

Now that we have everything, we calculate the cosine similarity.

### R Snippet of the problem

```text
> x <- c(8,9,0,1,3,3)
> y <- c(10,9,2,11,3,4)
> dot <- x%*%y
> norm.x <- sqrt(sum(x^2))
> norm.y <- sqrt(sum(y^2))
> cosine <- (dot) / (norm.x*norm.y)
> print(as.numeric(cosine))
[1] 0.8283643
```

The cosine similarity is often used to determine how similar two texts are. The approach involves creating a bag of words with the frequency of each term in the documents. Then, each "row" of terms is converted to a vector. For example, suppose we have two documents **X** and **Y**, and **X** says _"friday is my favorite day" \_and **Y**_ "mondays are my least favorite day". A bag of word would look like this:

| Doc. | friday | is | my | favorite | day | mondays | are | least |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| X | 1 | 1 | 1 | 1 | 1 | 0 | 0 | 0 |
| Y | 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 |

The vectorial representation would look like this:

 and .

