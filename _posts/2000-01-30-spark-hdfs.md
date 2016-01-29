---
title: "Spark + HDFS"
bg: orange
color: black
fa-icon: toggle-on
---

# Spark + HDFS?

Say, we have an AWS account and want to load a dataset into HDFS cluster and run an Apache Spark job to explore our data and learn some Spark for fun and profit. Setting the up the entire environment, with Apache Zeppelin as a shell for visualization and querying, running at scale can be as simple as:

{% highlight bash linenos=table %}
git clone https://github.com/pintostack/core.git pintostack-core
cd pintostack-core
export AWS_KEY=your-aws-key
./provision.sh --target=aws --masters=1 --slaves=5 # create 1 master and 5 slaves on AWS
./bootstrap-master.sh # install masters
./bootstrap-slave.sh # install slaves
./docker-push.sh docker/zeppelin # build docker image and push in into the registry
./docker-push.sh docker/hdfs
./marathon-push.sh marathon/hdfs-nn.json # push hd
./marathon-push.sh marathon/hdfs-dn.json
./marathon-push.sh marathon/zeppelin.json
{% endhighlight %}
