This is mini vgg implementation on CIFAR 10 dataset. There were multiple trials performed with different hyperparameter tuning to find the best forming model.
## Trials Performed
a) MiniVGG
Initially, original architecture was followed and the network was alarmingly overfitting. To address this, introduced BN, dropout and scheduler to stabilize the training and reduce overfitting. Below are the trials performed:
1) LR=0.003, weight_decay=0.008, Dropout(0.3) - Overfitting 2) LR=0.0003, weight_decay=0.008, Dropout(0.4) - Slightly underfitting suggesting that the dropout should be reduced 3) LR=0.0003, weight_decay=0.005, Dropout(0.3) = better convergence 4) LR=0.0008, weight_decay=0.005, Dropout(0.3) - good convergence
1
b) Variant1(UsingSeluandSwishActivation) SELU had the best test accuracy. Both SELU and Swish had desirable convergence for
the below parameters:
LR=0.0008, weight_decay=0.005, Dropout = 0.5 before the FC Layer
c) Variant2(RemovingMaxpoolLAyersandaddingStride=2)
* 		1)  LR = 0.0008 lower test accuracy but a good convergence. 
* 		2)  LR = 0.001 better test accuracy and good convergence. 
d) Variant3(AddingfewdropoutLayers)
* 		1)  PARTA:LR=0.0005,weight_decay=0.008,0.5dropoutbeforetheFClayer–better test accuracy and good convergence 
* 		2)  PARTB:LR=0.0005,weight_decay=0.008,dropoutaftereveryconvolutionlayer was 0.2, 0.3, 0.4 respectively —Overfitting 
* 		3)  LR=0.0005,weight_decay=0.008,dropoutaftereveryconvolutionlayerwas0.2, 0.2, 0.2 respectively – good convergence 
e) Variant 4
Initially the network was extremely underfitting, the only hyperparameter tuned here was the LR.
1) lr=0.0008, weight_decay=0.008 Alarmingly Underfitting 3) lr = 0.005 good test accuracy but slightly overfitting 4) lr == 0.001 underfitting 5) lr = 0.002, dropout = 0.1 – good test accuracy and convergence
