# What's a good API for ML?

## Speed vs usability

The above question is a simple looking but deceptively deep question. Fundamentally language is about building good abstractions to communicate efficiently. As far as programming languages are concerned we want to have ergonomic abstractions that make us productive but we don't want to sacrifice performance.

Here is an example for what a good API could look like courtesy from the [Keras documentation](https://www.tensorflow.org/alpha/guide/keras/overview)

```python
from tensorflow.keras import layers

model = tf.keras.Sequential()
# Adds a densely-connected layer with 64 units to the model:
model.add(layers.Dense(64, activation='relu'))
# Add another:
model.add(layers.Dense(64, activation='relu'))
# Add a softmax layer with 10 output units:
model.add(layers.Dense(10, activation='softmax'))
```

Keras has about 40K lines of Python code so it's probably not that cost effective for us to replicate the entire thing. But we can scope things to down to make the above example work in Rust.

Our checklist will be implementing
* Initializing sequential model
* Initializing a dense layer with custom size
* An interface activation function
* The ability to add functions

There's lots of key features missing here, namely ```model.fit()```, ```model.predict()```, ```model.save()``` and ```model.load()``` which I'm happy to also implement but hopefully we can agree that if we implement the checklist, we can convince ourselves that Rust can be an adequate language for deep learning.

## Porting Keras API to Rust

```rust
struct Sequential {
    layers: Vec<Layer>;
}

impl Sequential {
    fn add(&self, layer: Layer) -> Self {
        //do some typechecking on parameters here
    }
}
```

```rust
//should be an interface instead
struct Layer {
    dtype : f64, //should be able to support multiple data types using templates
    weights: ,
    input_nodes ,
    output_nodes,
}

impl Layer {
    fn get_input_at_node_index() {

    }

    fn assert_input_compatibility {

    }

    fn 
}
```

## Open items
* What's masking? Shows up a lot in the Keras codebase
* Maybe a whole tutorial, guide through Keras codebase could be worthwhile for people