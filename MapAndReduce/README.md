## Map and Reduce Section

There are 2 types of Map and Reduce Programs which I have made.

- Calculation of overall rating of different games based on platform.
- Calculation of overall rating of different games based on genre.

## Running
#### To run on local machine
```python
#Mapper1
python cat VideoGame.txt | python mapper1.py
#Mapper2
python cat VideoGame.txt | python mapper2.py
#Mapper And Reducer
python cat VideoGame.txt | python mapper1.py | sort -k1,1 | python reducer1.py 
python cat VideoGame.txt | python mapper2.py | sort -k1,1 | python reducer2.py 
```

#### To run on HADOOP FILESYSTEM
- Import the dataset from normal filesystem to hadoop filesystem.
```bash
hdfs dfs -put VideoGames.txt  /user/cloudera/
```
- Execute the program by giving them access to the STDIN and STDOUT methods.
```bash
hadoop jar /usr/lib/hadoop-0.20-mapreduce/contrib/streaming/hadoop-streaming-2.6.0-mr1-cdh5.13.0.jar -Dmapred.reduce.tasks=1 -file /home/cloudera/Desktop/MR-1/mapper.py /home/cloudera/Desktop/MR-1/reducer.py -mapper "python mapper.py" -reducer "python reducer.py" -input /user/cloudera/VideoGames.txt -output /user/cloudera/output1
```
- Check the output using
```bash
hdfs dfs -cat output1/part*
```






