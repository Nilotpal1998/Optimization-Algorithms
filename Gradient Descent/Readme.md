<h1><b>The Vanilla Gradient Descent / Batch Gradient Descent </b> </h1>
<h2> Optimization Goals </h2>
<p>Optimization refers maily to two basic concepts :-</p>
<p>1.Minimization</p>
<p>2.Maximization</p>
<p>of the objective function <b>f(x)</b> parameterised by our independent variable x. In the Machine/Deep Learning terminology we are endowed with task of minimizing the loss function <b>L(w)</b> parameterised by the model parametres .</p>
<p align="center">
  <img src="https://github.com/Nilotpal1998/Optimization-Algorithms/blob/main/Gradient%20Descent/gradient_images/chart1.jpg" width="550" title="Goal of Optimization">
</p>
<p>Mainly Optimization Algorithms have been endowed with the following Goals:-</p>
<p>1.Reaching the <b><i>Global Optima</i></b> </p>
<p>2. Reaching a <b><i>Local Optima</i> </b></p>
<p>Reaching the global optima is possible generally if the function is convex i.e any local minima is global minima . Whereas we are satisfied to be at the local minima of a neighbourhood if we are having the non convex scenario .</p>
<h2> The Gradient Descent </h2>
<p align="center">
  <img src="https://github.com/Nilotpal1998/Optimization-Algorithms/blob/main/Gradient%20Descent/gradient_images/1-1.gif" width="550" title="Gradient Descent Mechanism">
</p>
<p> Suppose we are considering our machine learning model we have some prediction by our model and we want to fit it in such a way that we can actually replicate and predict from our original scenario. So in order to do it we want minimize the difference between our actual and predicted / estimated function and in order to do that we calculate the loss as :- </p>
<p align="center">
  <img src="https://github.com/Nilotpal1998/Optimization-Algorithms/blob/main/Gradient%20Descent/gradient_images/loss.png" width="550" title="Loss Calculation">
</p>
<p>And we have to aim to minimize this error or loss.</p>
<h3>Algorithm</h3>
<p>1.Randomly initialize the starting point.</p>
<p>2.Update values :-</p>
<p align="center">
  <img src="https://github.com/Nilotpal1998/Optimization-Algorithms/blob/main/Gradient%20Descent/gradient_images/Update.png" width="550" title="Update Rule">
</p>
<p>3.Repeat until slope is zero.</p>
Thus or final result may be looking like this , <i>for our referal we have mainly considered the convex function</i>.
<h4>Result and Visualisation</h4>
<p align="center">
  <img src="https://github.com/Nilotpal1998/Optimization-Algorithms/blob/main/Gradient%20Descent/gradient_images/download.png" width="550" title="Update Rule">
</p>
<h3>Challenges</h3>
<p>1.Since the whole dataset has to be considered which involves a very high amount of computational complexity.</p>
<p>2.Chosing the learning rate remains another challenge in front of us because of two main reason :-</p>
<p><b>i.)</b>  If it is too small, then the model will take some time to learn.</p>

<p><b>ii.)</b>  If it is too large, model will converge as our pointer will shoot and we’ll not be able to get to minima.</p>

<p>3.A learning rate that is too low will lead to slow training and a higher learning rate will lead to overshooting of slope</p>
<p>Another key hurdle faced by Vanilla Gradient Descent is it avoid getting trapped in local minima; these local minimas are surrounded by hills of same error, which makes it really hard for vanilla Gradient Descent to escape it.</p>
<p>Thus there are many scopes of improvements and adjustments in this algoritm which will be explored in the coming contents of this very repository.</p>
