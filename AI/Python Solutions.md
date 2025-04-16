#MachineLearning 
#### By: Coursera - Mathematics for Machine Learning: PCA Week 1
---
### Numpy's Testing Module 
Numpy has a very useful function called [np.testing.assert_allclose()](https://numpy.org/doc/stable/reference/generated/numpy.testing.assert_allclose.html) which allows us to test our functions.

The function accepts two numbers or two Numpy arrays and checks them for equality. Note that you cannot compare floating point numbers using the `==` operator as you have to account for a margin of error which can be caused due to rounding. This function allows you to customize the error margin based on your needs.

We highly advice you to read the documentation of this function.
### Sigmoid Function
A ***Sigmoid Function*** is a mathematical function that has an "S" shaped curve. It is a very important function in ***Machine Learning***, statistics and biology. The most common form of it is the **logistic function**, which is defined as:
$$
S(x) = \frac{1}{1+e^{-x}}
$$
```graph
bounds: [-5,3,5,-3]
elements: [
	{type: slider, def: [[-4.5,2],[-2,2],[-3,1,3]], att: {name: "n"}},
	{type: slider, def: [[-4.5,1],[-2,1],[-3,1,3]], att: {name: "a"}},
	{type: slider, def: [[-4.5,-1],[-1,-1],[-3,0,3]], att: {name: "s"}},
	{type: functiongraph, def: ["f:e0/(e1 + 2.71828**-x) + e2"], att: {strokeWidth: 4, strokeColor: red, dash: 3}},
]
```

##### Key Characteristics

1. **Range**: The output of the sigmoid function ranges between $0$ and $1$. This makes it particularly useful for models that need to predict probabilities.

2. **Shape**: The curve is smooth and continuous, with a horizontal asymptote at both $0$ and $1$. As $x$ approaches negative infinity, $S(x)$ approaches $0$, and as $x$ approaches positive infinity, $S(x)$ approaches $1$.
   
3. **Derivative**: The derivative of the sigmoid function can be expressed in terms of the function itself:
$$
S′(x)=S(x)(1−S(x))
$$
   This property is useful in optimization algorithms, such as gradient descent, as it simplifies the computation of gradients.

4. **Applications**: Sigmoid functions are widely used in logistic regression, neural networks (as activation functions), and in modeling growth processes in biology.
##### Simple Python Numpy Implementation
```python
def sigmoid(x):
    """
    Computes the sigmoid of x

    Arguments:
    x: A real number or a Numpy array

    Returns:
    s: The sigmoid of x
    """
    
    s = 1 / ( 1 + np.exp(-x))

    return s

x = 2.1
expected = 0.8909031
np.testing.assert_allclose(sigmoid(x), expected, rtol=1e-5)

x = np.array([[3.4, -7.1, 9.4],
              [-2.7, 8.882, -2.114]])
expected = np.array([[9.67704535e-01, 8.24424686e-04, 9.99917283e-01],
                     [6.29733561e-02, 9.99861153e-01, 1.07743524e-01]])
np.testing.assert_allclose(sigmoid(x), expected, rtol=1e-5)

print("All tests passed!")
```
### Normalizing Array Columns
Before a machine learning model is applied to data, it is very common to first normalize it. Suppose that $𝑥_{i}$ is the $i^{th}$ column of the input array, and $c_{i}$ is the $i^{th}$ column of the output array, then:
$$
c_{i} = \frac{x_{i} - E[x_{i}]}{\sigma(x_{i})}
$$
$\text{Where:}$
$E[x_{i}]: \text{Algebraic mean of all elements of }x_{i}$
$\sigma(x_{i}): \text{Standard deviation of all elements of }x_{i}$

Here's a Python implementation using numpy:
```python
def normalize(x):
    """
    Normalize all the columns of x

    Arguments:
    x: A two dimensional Numpy array

    Returns:
    c: The normalized version of x
    """

    # Calculate the mean of all columns
    mean = np.mean(x, axis=0)

    # Calculate the standard deviation all columns
    sigma = np.std(x, axis=0)

    # Compute the final answer
    c = (x - mean) / sigma

    return c

x = np.array([[1, 4],
              [3, 2]])
expected = np.array([[-1, 1],
                     [1, -1]])

print(normalize(x))
np.testing.assert_allclose(normalize(x), expected, rtol=1e-5)

x = np.array([[324.33, 136.11, 239.38, 237.17],
              [123.43, 325.24, 243.52, 745.25],
              [856.36, 903.02, 430.25, 531.35]])
expected = np.array([[-0.35694152, -0.97689929, -0.73023324, -1.28391946],
                     [-1.00662188, -0.39712973, -0.68372539,  1.1554411 ],
                     [ 1.3635634 ,  1.37402902,  1.41395863,  0.12847837]])
np.testing.assert_allclose(normalize(x), expected, rtol=1e-5)

print("All tests passed!")
```
### Image Dataset Visualization
When your dataset are **images**, it's a really good idea to see what they look like.

One very convenient tool in Jupyter is the `interact` widget, which we use to visualize the images (faces). For more information on how to use interact, have a look at the documentation [here](http://ipywidgets.readthedocs.io/en/stable/examples/Using%20Interact.html).

```python
from ipywidgets import interact

def show_face(face):
    plt.figure()
    # For image shape of 64x64
    plt.imshow(face.reshape((64, 64)), cmap='gray')
    plt.show()

@interact(n=(0, len(faces)-1))
def display_faces(n=0):
    plt.figure()
    plt.imshow(faces[n].reshape((64, 64)), cmap='gray')
    plt.show()
```
