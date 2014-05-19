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
import the project .RData fristly.
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

1.  data(Reuters21578) #import the data 	<br/>
rt <- preProcess(Reuters21578);# processing the data by using function in tm <br/>

2. get topics set <br/>
query <- " TOPICS == 'YES' & LEWISSPLIT == 'TRAIN' ";<br/>
trainSet <- tm_filter(rt, FUN = sFilter,query);<br/>
test set<br/>
query <- " TOPICS == 'YES' & LEWISSPLIT == 'TEST' ";<br/>
testSet <- tm_filter(rt, FUN = sFilter,query);<br/>
build up the topic set <br/>
earn.train <- trainSet[topicFilter(trainSet, 'earn', TRUE)]<br/>
acq.train <- trainSet[topicFilter(trainSet, 'acq', TRUE)]<br/>
moneyfx.train <- trainSet[topicFilter(trainSet, 'money-fx', TRUE)]<br/>
grain.train <- trainSet[topicFilter(trainSet, 'grain', TRUE)]<br/>
crude.train <- trainSet[topicFilter(trainSet, 'crude', TRUE)]<br/>
trade.train <- trainSet[topicFilter(trainSet, 'trade', TRUE)]<br/>
interest.train <- trainSet[topicFilter(trainSet, 'interest', TRUE)]<br/>
ship.train <- trainSet[topicFilter(trainSet, 'ship', TRUE)]<br/>
wheat.train <- trainSet[topicFilter(trainSet, 'wheat', TRUE)]<br/>
cron.train <- trainSet[topicFilter(trainSet, 'corn', TRUE)]<br/>


3. kNN<br/>
testKNN( total.dic.matrix,total.dic.matrix, total.dic.matrix.row, all.class.length.train, all.class.name.train)<br/>
testKNN( total.dic.test.matrix,total.dic.test.matrix, total.dic.test.matrix.row, all.class.length.test,<br/> all.class.name.train)<br/>
result<br/>
[1] "...total...."<br/>
[1] 2787
[1] "...success ...."<br/>
[1] 2787<br/>
[1] "...error...."<br/>
[1] 0<br/>

4. svm<br/>
ksvm <- ksvm(type ~ ., data = total.df.train)<br/>
pred.ksvm <- predict(ksvm, total.df.train)<br/>
table(pred.ksvm ,total.df.train$type)<br/>

5. naiveBayes<br/>
model.nb <- naiveBayes(type ~ ., data = total.df.train)<br/>
pred.nb <- predict(ksvm, total.df.train)<br/>
table(pred.nb ,total.df.train$type)<br/>
earn.total.train.nb <-  nbGetClass(total.train, dic.train, all.class.name.train);<br/>

5. cluster<br/>
clustering.data.scale <- scale(clustering.df.train);<br/>
clustering.d <- dist(clustering.data.scale,method = "euclidean");<br/>
clustering.fit <- hclust(clustering.d,method = "ward");<br/>
plot(clustering.fit);<br/>
train.kmeans <- kmeans(total.dic.test.matrix, 10);<br/>
type = rep(1:10,times= all.class.length.test)<br/>
table(type, train.kmeans$cluster)<br/>

