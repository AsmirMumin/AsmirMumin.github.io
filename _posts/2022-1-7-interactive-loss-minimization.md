---
layout: prediction_post
published: True
title: Interactive Machine Learning Session
---

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

<script type="text/javascript" src="/js/nnVizUtils.js"></script>
<!-- Visualizations 1 Weight & bias, and 2 Gradient Descent -->
<script type="text/javascript" src="/js/simple_nn.js"></script>
<!-- Visualization 3 - Two variables -->
<script type="text/javascript" src="/js/two_variable_nn.js"></script>
<!-- Visualization 4 - Features & classes -->
<script type="text/javascript" src="/js/shallow_nn_grapher.js"></script>