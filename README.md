# RL-for-binary-computation-offloading-in-wireless-powered-MEC-networks
It's a implementation about the paper Liang Huang, Suzhi Bi, and Ying-jun Angela Zhang, "Deep Reinforcement Learning for Online Computation Offloading in Wireless Powered Mobile-Edge Computing Networks", on https://ieeexplore.ieee.org/document/8771176
But I've modified some parameters and the number of neurons in the decoder network, and I switch the decoder method to 'K nearest neighbor'.
This work considered a wireless powered mobile edge-computing network that follows binary offloading policy. That is, each computation is either computed on the energy harvesting WD or offloaded to an server(AP). The goal of DROO is to optimize the offloading decisions and allocate the resouces according to the channel conditions(channel gain)

## Performance
-The train loss and the test loss. In fact it's validation loss cause I calculate it during training phase. In addition, the decoder never seen these data.
<img src="https://github.com/jordan8409212/RL-for-binary-computation-offloading-in-wireless-powered-MEC-networks/blob/master/result/Training%20and%20test%20loss%20separately.jpeg" width = "400" height = "260" alt="train" 
align=center>
-The nomalized computation rate during training 
the nomalized computation rate is defined as follows
&\hat Q(\textbf{h},\textbf{x})=\frac{Q^*(\textbf{h},\textbf{x})}{\max\limits_{\textbf{x}'\in\{0,1\}^N}Q^*(\textbf{h},\textbf{x}')}\\
&\hat Q(\textbf{h},\textbf{x})\in [0,1]
The blue curve denotes the moving average of $\hat{Q}$ over the last 50 time frames, and the
light blue shadow denotes the maximum and minimum of $\hat{Q}$ in the last 50 frames.
<img src="https://github.com/jordan8409212/RL-for-binary-computation-offloading-in-wireless-powered-MEC-networks/blob/master/result/Normalized%20computation%20rate(training).jpeg" width = "400" height = "260" alt="train" 
align=center>
## Data 
The folder includs all pre-generated training and testing data set, including:

- **data_#.mat**: , where # = {10, 20, 30} is the number of WDs

Data samples are generated by enumerating all 2^N binary offloading actions for N <= 10 and by following the CD method presented in https://ieeexplore.ieee.org/document/8334188 for N = 20, 30. There are 30,000 (for N = 10, 20, 30) or 10,000 (otherwise) samples saved in each \*.mat file. Where each data sample includes:

|      variable          |    description            |
|------------------------:|:-----------------------|
|     input_h           |  The wireless channel gain between WDs and the AP   $\mathbf{h}$        |         
|     output_mode        |  The optimal binary offloading action  $\mathbf{x}^*$      |    
|      output_a           | The optimal fraction of time that the AP broadcasts RF energy for the WDs to harvest  $a^*$ |    
|    output_tau         | The optimal fraction of time allocated to WDs for task offloading $\mathbf{\tau}^*$|    
|      output_obj         | The optimal weighted sum computation rate $Q^*$   |   



