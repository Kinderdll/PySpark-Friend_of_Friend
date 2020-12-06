
# Setup environment
Well in windows there are plenty of shitty steps

Install Java , SET PATH
Install Python , SET PATH
(Hadoop workaround)Donwload winutils.exe (substitute for hadoop,as spark needs hadoop), SET PATH "C:\winutils\bin
Download spark ,SET PATH  for pyspark to work properly(C:\spark\bin)
    ~In case constructors fail ,upgrade pyspark (got spark 3.01, pyspark 3.01)

Vagrant guidelines:
    make sure spark is up , hadoop is up (ps aux|grep spark or hadoop)
    otherwise hadoop\sbin\start-all.sh spark\sbin\start-all.sh
    


#How to create an virtual environment (make sure virtual env modue is isntalled)
```
virtualenv -p python3 .venv //creates .venv virtual environment so to get all deps like pyspark
source .venv/bin/activate  or source .venv/Scripts/activate for Windows Users

pip3 install -r requirements.txt
```

# Call locally

```
./fof.py --input ../input/out.ego-facebook --output output --master "local[4]"
```

# Submit to spark 

```
spark-submit --master local[*] fof.py --input input --output output
```

or 

```

make sure output is unique directory (otherwise delete or create new output dir)
spark/bin/spark-submit /vagrant/data/example2/fof-python/fof.py --input hdfs://localhost:54310/fof/input --output hdfs://localhost:54310/fof/output
```
