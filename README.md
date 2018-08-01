# Linear-Learn-in-TensorFlow.js


```js

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <script src="https://cdn.jsdelivr.net/npm/@tensorflow/tfjs"> </script>
</head>
<body>

    <div id="output"></div>
    

    <script>
        async function LearnLinear() {
            const model = tf.sequential();
            model.add(tf.layers.dense({units:1, inputShape: [1]}))

            model.compile({
                loss:'meanSquaredError',
                optimizer:'sgd'
            });

            const xs = tf.tensor2d([0, 1, 2, 3, 4, 5], [6, 1]);
            const ys = tf.tensor2d([0, 1, 2, 3, 4, 5], [6, 1]);

            await model.fit(xs,ys,{epochs:250});

            document.getElementById('output').innerHTML = model.predict(tf.tensor2d([6], [1, 1]));
        }

        LearnLinear();
    </script>
</body>
</html>

```
