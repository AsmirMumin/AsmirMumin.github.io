---
layout: prediction_post
published: True
title: Interactive Machine Learning Session - Practical House Price Example
---

## Interactive Machine Learning Session - Practical House Price Example

Let's start with a simple example. Say you're helping a friend who wants to buy a house. She was quoted $400,000 for a 2000 sq ft house (185 meters). Is this a good price or not?

It's not easy to tell without a frame of reference. So you ask your friends who have bought houses in that same neighborhoods, and you end up with three data points:


{::options parse_block_html="true" /}
<div class="one_variable">

 | Area (sq ft) (x) | Price (y) |
 | --- | --- |
 | 2,104 | 399,900 |
 | 1,600 | 329,900 |
 | 2,400 | 369,000 |

</div>

Personally, my first instinct would be to get the average price per sq ft. That comes to $180 per sq ft.

Welcome to your first neural network! And it looks like this:


<div class="img-div" markdown="0">
    <img src="/images/simple_NN_1.png" />
</div>

Diagrams like this show you the structure of the network and how it calculates a prediction. The calculation starts from the input node at the left. The input value flows to the right. It gets multiplied by the weight and the result becomes our output.

<div class="img-div" markdown="0">
    <img src="/images/NNs_formula_no_bias.png" />
</div>

This is a form of prediction. This is a simple predictive model that takes an input, does a calculation, and gives an output (since the output can be of continuous values, the technical name for what we have would be a "regression model")

Let us visualize this process (for simplicity, let's switch our price unit from $1 to $1000. Now our weight is 0.180 rather than 180):

<p class="gif-space"/>

![]({{site.baseurl}}/images/data_points_graph_animated.gif)

<p class="gif-space"/>

<p class="gif-space"/>

## Let´s improve this

Can we do better than estimate the price based on the average of our data points? Let's try. Let's first define what it means to be better in this scenario. If we apply our model to the three data points we have, how good of a job would it do?


<p class="gif-space"/>

![]({{site.baseurl}}/images/data_points_error_animated.gif)

<p class="gif-space"/>

That's quite a bit of yellow. Yellow is bad. Yellow is error. We want to shrink yellow as much as we can.



{::options parse_block_html="true" /}
<div class="one_variable">

<div class="one_variable">

  <table>
    <thead>
      <tr>
        <th>Area (x)</th>
        <th>Price ($1000) (<span class="y_">y_</span>)</th>
        <th>Prediction (<span class="y">y</span>)</th>
        <th><span class="y_">y_</span>-<span class="y">y</span></th>
        <th>(<span class="y_">y_</span>-<span class="y">y</span>)²</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>2,104</td>
        <td>399.9</td>
        <td>379</td>
        <td>21</td>
        <td>449</td>
      </tr>
      <tr>
        <td>1,600</td>
        <td>329.9</td>
        <td>288</td>
        <td>42</td>
        <td>1756</td>
      </tr>
      <tr>
        <td>2,400</td>
        <td>369</td>
        <td>432</td>
        <td>-63</td>
        <td>3969</td>
      </tr>
      <tr>
        <td> </td>
        <td> </td>
        <td colspan="2" align="right"><span class="total"> Average:</span></td>
        <td><b>2,058</b></td>
      </tr>
    </tbody>
  </table>

</div>




</div>


Now that we defined our measuring stick for what makes a better model, let's experiment with a couple more weight values and compare them with our average pick:
 

<p class="gif-space" />

![]({{site.baseurl}}/images/lines_and_errors_animated.gif)

<div class="img-div" markdown="0">
We can't improve much on the model by varying the weight any more. But if we add a bias we can find values that improve the model.
</div>
<p class="gif-space" />


Our lines can better approximate our values now that we have this b value added to the line formula. In this context, we call it a "bias". This makes our neural network look like this:




<div class="img-div" markdown="0">
    <img src="/images/NNs_bias.png" />
</div>





We can generalize it by saying that a neural network with one input and one output (*spoiler warning:* and no hidden layers) looks like this:




<div class="img-div" markdown="0">
    <img src="/images/NNs_bias_2.png" />
</div>
In this graph, W and b are values we find during the training process. X is the input we plug into the formula (area in sq ft in our example). Y is the predicted price.



Calculating a prediction now uses this formula:



<div class="img-div" markdown="0">
    <img src="/images/NNs_formula.png" />
</div>



So our current model calculates predictions by plugging in the area of house as x in this formula:




<div class="img-div" markdown="0">
    <img src="/images/NNs_formula_ex.png" />
</div>


## Try it out!
How about you take a crack at training our toy neural network? Minimize the loss function by tweaking the weight and bias dials. Can you get an error value below 799?


<div id="training-one-chart" class="training-chart"/>
<table id="training-one" class="training-table">
    <tr>
        <td>
            Error
        </td>
        <td colspan="2">
            <span id="error-value" ></span>
        </td>
    </tr>
    <tr>
        <td class="error-cell" colspan="3">
            <span id="error-value-message"></span>&nbsp;
        </td>
    </tr>
    <tr>
        <td>
            Weight
        </td>
        <td>
            <input id="weightSlider" type="range" class="weight" min="0" max="0.4" step="0.001" >
        </td>
        <td class="slider-value">
            <span id="weight" class="weight">0</span>
        </td>
    </tr>
    <tr>
        <td>
            Bias
        </td>
        <td>
            <input id="biasSlider" type="range" class="bias"  min="0" max="460" step="1" >
        </td>
        <td class="slider-value">
            <span id="bias" class="bias">0</span>
        </td>
    </tr>
</table>

<div id="neural-network-graph" class="nn-graph-area" ></div>




## Automation
Congratulations on manually training your first neural network! Let's look at how to automate this training process. Below is another example with an additional autopilot-like functionality. These are the GD Step buttons. They use an algorithm called "Gradient Descent" to try to step towards the correct weight and bias values that minimize the loss function.


<div class="container"  markdown="0">
    <div class="row">

        <div class="col-sm-6 graphs">
            <div id="training-one-gd-chart" class="training-chart" ></div>


                <div class="row training-chart mini-charts">
                    <div id="training-one-gd-error-chart" class="error-chart col-xs-6" ></div>
                    <div id="training-one-gd-heatmap" class="error-chart col-xs-6" ></div>
                </div>

        </div>

        <div class="col-sm-6">

            <table id="training-one-gd" class="training-table">
                <tr>
                    <td colspan="3" class="gd-buttons">
                        <input type="button" value="GD Step" id="gradient-descent-button"  class="btn btn-primary" />
                        <input type="button" value="10 GD Steps " id="gradient-descent-10-button"  class="btn btn-primary" />
                        <input type="button" value="100 GD Steps " id="gradient-descent-100-button"  class="btn btn-primary" />
                    </td>
                </tr>
                <tr>
                    <td>
                        Error
                    </td>
                    <td colspan="2">
                        <span id="error-value" ></span>
                    </td>

                </tr>

                <tr>
                    <td class="error-cell" colspan="3">
                        <span id="error-value-message"></span>&nbsp;
                    </td>

                </tr>
                <tr>
                    <td>
                        Weight
                    </td>
                    <td>
                        <input id="weightSlider" type="range" class="weight" min="0" max="0.4" step="0.0001">
                    </td>
                    <td class="slider-value">
                        <span id="weight" class="weight">0</span>
                    </td>
                </tr>
                <tr>
                    <td>
                        Bias
                    </td>
                    <td>
                        <input id="biasSlider" type="range"  class="bias" min="0" max="460" step="0.1">
                    </td>
                    <td class="slider-value">
                        <span id="bias" class="bias">0</span>
                    </td>
                </tr>
            </table>

            <div id="neural-network-gd-graph" class="nn-graph-area" ></div>
        </div>
    </div>
</div>

The two new graphs are to help you track the error values as you fiddle with the parameters (weight and bias) of the model. It's important to keep track of the error as the training process is all about reducing this error as much possible.

How does gradient descent know where its next step should be? Calculus. You see, knowing the function we're minimizing (our loss function, the average of (y_ - y)² for all our data points), and knowing the current inputs into it (the current weight and bias), the derivatives of the loss function tell us which direction to nudge W and b in order to minimize the error.