# Benchmarking and Analysis of Network Functions

### Overview 
 
This project is a part of Master's curriculum. More details about the project can be found [here](https://en.cs.uni-paderborn.de/cn/teaching/theses-student-projects/student-project-groups-completed/ba). Network Function Virtualization (NFV) is a concept of making the network functions more flexible and manageable. Network functions such as proxy, load balancer etc. can be installed using container technology to meet the user demands. Such network functions are called Virtual Network Functions (VNFs).The main objective of the project is to The collected dataset and publish it to make it available for the research communities since there are very limited VNF performance profiles available. I was a part of benchmarking and analysis team where I was more inclined towards analysis of the data.  I worked on 2 network services namely Traefik and mitmproxy. However, here I give a brief overview and analysis of Traefik.

Traefik is an open-source Edge router that acts as a load balancer and a reverse proxy for TCP and HTTP-based applications and it can be configured automatically as well as manually. Traefik integrates easily with every major cluster technology such as Docker. I concentrated on configuring traefik as a load balancer and it is installed as an Ubuntu-based docker image to balance the incoming load among web servers. This experiment is also extended for the first time to use multiple connection points in tng-bench at the output. The experiment has been run under two different scenarios to compare the performance of VNF under various circumstances.


### Key outcomes

<ol>
<li> Created docker images for network services </li>
<li> Benchmarked the network services under various scenarios using a benchmarking tool called Tango-bench </li>
<li> Collected datasets which are then used for extensive exploratory data analysis </li>
<li> Analysed trends and patterns against different network services of same category for e.g. how do different load balancers such as NGINX, HAproxy, Traefik compare against        each other in terms of response time, handling requests per second etc.? </li>
<li> Extended the analysis to perform predictive analytics using Linear regression, random forest, SVM </li>
</ol>

### Analysis

##### Correlation matrix of traefik

Correlation helps in identifying the relationship between the variables. Having a more positive values indicates that the parameters are highly correlated and vice versa.

![](https://github.com/ishriya/benchmarking-and-analysis-of-network-functions/blob/main/load_balancers/correlation_traefik.PNG)

##### Comparison of traefik with other load balancers

![](https://github.com/ishriya/benchmarking-and-analysis-of-network-functions/blob/main/load_balancers/mean_time.PNG)

######  Observation: 
It is the time taken to respond to a request for service.  Having the least response time indicates better performance of a load balancers. According to the plot, the response time of NGINX is the least among others which means that it gives the quickest response for a request. This could be due to default caching in NGINX which other load balancers does not have. Traefik takes more time to respond to a request. A general trend is seen for all the load balancers - as the CPU bandwidth increases the mean time per request decreases.

##### Predictions

The predominant aim of using prediction models is to predict the required physical resources for a network service. Various regression techniques such as linear, random forest, SVM are tested.

![](https://github.com/ishriya/benchmarking-and-analysis-of-network-functions/blob/main/predictions/Linear_regression.png)
![](https://github.com/ishriya/benchmarking-and-analysis-of-network-functions/blob/main/predictions/Random_forest.png)
![](https://github.com/ishriya/benchmarking-and-analysis-of-network-functions/blob/main/predictions/SVM.png)

#### Comparing the prediction models

MSE, RMSE, MAE are error metrics which are used to compare the accuracy of the prediction models. According to the results, random forest performed better on the collected data set and very less prone to errors as compared to other prediction models. I concluded that random forest performs best for the collected data set of traefik and it can be used to predict the required resources. However, there is always room for improvement. There could be other models which may perform better than random forest.

![](https://github.com/ishriya/benchmarking-and-analysis-of-network-functions/blob/main/predictions/comparison.png)


