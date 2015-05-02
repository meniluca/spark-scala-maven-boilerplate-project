### Instructions:

[Follow this article to find more detailed instructions.](https://nosqlnocry.wordpress.com/2015/02/27/how-to-build-a-spark-fat-jar-in-scala-and-submit-a-job/)

Modify the class "MainExample.scala" writing your Spark code, then compile the project with the command:

```mvn clean package```

Inside the ```/target``` folder you will find the result fat jar called ```spark-scala-maven-project-0.0.1-SNAPSHOT-jar-with-depencencies.jar```. In order to launch the Spark job use this command in a shell with a configured Spark environment:

    spark-submit --class com.examples.MainExample \
      --master yarn-cluster \
      spark-scala-maven-project-0.0.1-SNAPSHOT-jar-with-depencencies.jar \
      inputhdfspath \
      outputhdfspath

The parameters ```inputhdfspath``` and ```outputhdfspath``` don't have to present the form ```hdfs://path/to/your/file``` but directly ```/path/to/your/files/``` because submitting a job the default file system is HDFS. To retrieve the result locally:

    hadoop fs -getmerge outputhdfspath resultSavedLocally
