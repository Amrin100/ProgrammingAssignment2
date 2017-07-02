## Function **makeCacheMatrix()** create a list to

## set the value of the matrix via function *set()*
## get the value of the matrix via function *get()*
## set the value of the inverse matrix via function *setInverse()*
##get the value of the inverse matrix via function *getInverse*

## makeCacheMatrix() 

makeCacheMatrix <- function(x = matrix()) {
  m <- NULL
  set <- function(y) {
    x <<- y
    m <<- NULL
  }
  get <- function() x
  setInverse <- function(inverse) m <<- inverse
  getInverse <- function() m
  list(set = set, get = get,
       setInverse = setInverse,getInverse = getInverse)
}

## Function **cacheSolve()** calculates the inverse of the matrix passed by **makeCacheMatrix()**

cacheSolve <- function(x, ...) {
  m <- x$getInverse()
  if(!is.null(m)) {
    message("getting cached data")
    return(m)
  }
  data <- x$get()
  m <- solve(data, ...)
  x$setInverse(m)
  m
}


B <- matrix(1:4,2,2)
BB <- makeCacheMatrix(B)
BB

{r}
cacheSolve(BB)

