---
layout: prediction_post
published: True
title: Interactive Loss Minimization
---


<div class="img-div" markdown="0">
    <img src="/images/simple_NN_1.png" />
</div>

## Motivation

This post contains an interactive graphs to demonstrate what weights and biases are and how their respective errors while model training are minimized. 

<!--more-->

## House Price Example

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


## Playground!
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




<script type="text/javascript" src="/js/nnVizUtils.js"></script>
<!-- Visualizations 1 Weight & bias, and 2 Gradient Descent -->
<script type="text/javascript" src="/js/simple_nn.js"></script>
<!-- Visualization 3 - Two variables -->
<script type="text/javascript" src="/js/two_variable_nn.js"></script>
<!-- Visualization 4 - Features & classes -->
<script type="text/javascript" src="/js/shallow_nn_grapher.js"></script>