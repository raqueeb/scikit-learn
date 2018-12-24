# কোডে প্রথম মডেল

এস্টিমেটরের কাজের ধাপের পুরো কোড এখানে। না বুঝলে আবার ফিরে যান "এস্টিমেটরের কাজের ধাপ" চ্যাপ্টারে। 

```python
# import load_iris function from datasets module
from sklearn.datasets import load_iris

# save "bunch" object containing iris dataset and its attributes
iris = load_iris()

# store feature matrix in "X"
X = iris.data

# store response vector in "y"
y = iris.target
```

```python
from sklearn.neighbors import KNeighborsClassifier
```

```python
knn = KNeighborsClassifier
```

```python
print(knn)
```

```python
knn = KNeighborsClassifier(n_neighbors=1)
```

```python
knn
```

```text
KNeighborsClassifier(algorithm='auto', leaf_size=30, metric='minkowski',
           metric_params=None, n_jobs=1, n_neighbors=1, p=2,
           weights='uniform')
```

```python
knn.fit(X, y)
```

```text
KNeighborsClassifier(algorithm='auto', leaf_size=30, metric='minkowski',
           metric_params=None, n_jobs=1, n_neighbors=1, p=2,
           weights='uniform')
```

```python
knn.predict([[3, 5, 4, 2]])
```

```text
array([2])
```

```python
knn.
```

