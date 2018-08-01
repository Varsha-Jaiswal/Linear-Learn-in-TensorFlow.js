# Linear-Learn-in-TensorFlow.js

In this case I get a number of (X,Y) points and use that to train a Machine Learned model that can then infer the linear relationship between them. Thus, when I give a future X value, it’s able to derive the Y for that X. It’s a really simplistic scenario, but it gives you the basics for how Machine Learning works — by using training data, a neural network can derive the relationships between them, and those relationships can be used to predict or classify new values. 

```js

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    
    <!-- Load TensorFlow.js -->
    <script src="https://cdn.jsdelivr.net/npm/@tensorflow/tfjs"> </script>
</head>
<body>

    <div id="output"></div>
    

    <script>
        async function LearnLinear() {
            // Define a model for linear regression.
            const model = tf.sequential();
            model.add(tf.layers.dense({units:1, inputShape: [1]}))

            // Prepare the model for training: Specify the loss and the optimizer.
            model.compile({
                loss:'meanSquaredError',
                optimizer:'sgd'
            });

            // Generate some synthetic data for training.
            const xs = tf.tensor2d([0, 1, 2, 3, 4, 5], [6, 1]);
            const ys = tf.tensor2d([0, 1, 2, 3, 4, 5], [6, 1]);

            // Train the model using the data.
            await model.fit(xs,ys,{epochs:250});

            // Use the model to do inference on a data point the model hasn't seen before:
            document.getElementById('output').innerHTML = model.predict(tf.tensor2d([6], [1, 1]));
        }

        LearnLinear();
    </script>
</body>
</html>

```
