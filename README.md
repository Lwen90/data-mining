<h1>data-mining<h1>

<h2>content<h2>
<p>kNN<br/>
naiveBayes<br/>
svm<br/>
kmeans<br/>
hierarchy cluster<br/>
<p>

<h2>required library </h2>
<p>
e1071, tm, kknn, ROCR, kernlab etc.<br/>
import the project .RData fristly.<br/>
</p>


<h2>Steps </h2>
<p>
1. import the data and processing using tm. <br/>
2. filter to get topic training set and testing set.<br/>
3. get features through getting the frequent terms.<br/>
4. building the classify and evaluating.<br/>
5. buding the cluster and evaluating.<br/>

</p>

<h2>examples </h2>

1.  data(Reuters21578) #import the data 	
rt <- preProcess(Reuters21578);# processing the data by using function in tm 

2. get topics set 
query <- " TOPICS == 'YES' & LEWISSPLIT == 'TRAIN' ";
trainSet <- tm_filter(rt, FUN = sFilter,query);
test set
query <- " TOPICS == 'YES' & LEWISSPLIT == 'TEST' ";
testSet <- tm_filter(rt, FUN = sFilter,query);
build up the topic set 
earn.train <- trainSet[topicFilter(trainSet, 'earn', TRUE)]
acq.train <- trainSet[topicFilter(trainSet, 'acq', TRUE)]
moneyfx.train <- trainSet[topicFilter(trainSet, 'money-fx', TRUE)]
grain.train <- trainSet[topicFilter(trainSet, 'grain', TRUE)]
crude.train <- trainSet[topicFilter(trainSet, 'crude', TRUE)]
trade.train <- trainSet[topicFilter(trainSet, 'trade', TRUE)]
interest.train <- trainSet[topicFilter(trainSet, 'interest', TRUE)]
ship.train <- trainSet[topicFilter(trainSet, 'ship', TRUE)]
wheat.train <- trainSet[topicFilter(trainSet, 'wheat', TRUE)]
cron.train <- trainSet[topicFilter(trainSet, 'corn', TRUE)]


3. kNN
testKNN( total.dic.matrix,total.dic.matrix, total.dic.matrix.row, all.class.length.train, all.class.name.train)
testKNN( total.dic.test.matrix,total.dic.test.matrix, total.dic.test.matrix.row, all.class.length.test, all.class.name.train)
result
[1] "...total...."
[1] 2787
[1] "...success ...."
[1] 2787
[1] "...error...."
[1] 0

4. svm
ksvm <- ksvm(type ~ ., data = total.df.train)
pred.ksvm <- predict(ksvm, total.df.train)
table(pred.ksvm ,total.df.train$type)

5. naiveBayes
model.nb <- naiveBayes(type ~ ., data = total.df.train)
pred.nb <- predict(ksvm, total.df.train)
table(pred.nb ,total.df.train$type)
earn.total.train.nb <-  nbGetClass(total.train, dic.train, all.class.name.train);

5. cluster
clustering.data.scale <- scale(clustering.df.train);
clustering.d <- dist(clustering.data.scale,method = "euclidean");
clustering.fit <- hclust(clustering.d,method = "ward");
plot(clustering.fit);
train.kmeans <- kmeans(total.dic.test.matrix, 10);
type = rep(1:10,times= all.class.length.test)
table(type, train.kmeans$cluster)

