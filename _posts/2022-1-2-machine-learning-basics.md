## Start here
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

Welcome to your first neural network! Now it's not quite at Siri level yet, but now you know the fundamental building block. And it looks like this:


<div class="img-div" markdown="0">
    <img src="/images/simple_NN_1.png" />
</div>

This is a form of prediction. This is a simple predictive model that takes an input, does a calculation, and gives an output (since the output can be of continuous values, the technical name for what we have would be a "regression model")

Let us visualize this process (for simplicity, let's switch our price unit from $1 to $1000. Now our weight is 0.180 rather than 180):

<p class="gif-space"/>

![]({{site.baseurl}}/images/data_points_graph_animated.gif)

<p class="gif-space"/>

<p class="gif-space"/>

## Harder, Better, Faster, Stronger

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
