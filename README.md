# Getting start

** Instalação do hadoop **

## Parte 0

Verificando a versão do Java

java -version

tar -xzvf hadoop-2.6.0-cdh5.8.2.tar.gz

Move para a pasta onde ficam o programas locais

sudo mv hadoop-2.6.0-cdh5.8.2 /usr/local/hadoop

Descobindo o PATH do JAVA_HOME

readlink -f /usr/bin/java | sed "s:bin/java::"

Output
/usr/lib/jvm/java-11-openjdk-amd64/


sudo nano /usr/local/hadoop/etc/hadoop/hadoop-env.sh

#export JAVA_HOME=${JAVA_HOME}
export JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64/

Para rodar o hadoop

/usr/local/hadoop/bin/hadoop

Output
Usage: hadoop [OPTIONS] SUBCOMMAND [SUBCOMMAND OPTIONS]
 or    hadoop [OPTIONS] CLASSNAME [CLASSNAME OPTIONS]
  where CLASSNAME is a user-provided Java class

  OPTIONS is none or any of:

--config dir                     Hadoop config directory
--debug                          turn on shell script debug mode
--help                           usage information
buildpaths                       attempt to add class files from build tree
hostnames list[,of,host,names]   hosts to use in slave mode
hosts filename                   list of hosts to use in slave mode
loglevel level                   set the log4j level for this command
workers                          turn on worker mode

  SUBCOMMAND is one of:
. . .

[TESTE] Rodando o exemplo do pi

/usr/local/hadoop/bin/hadoop jar /usr/local/hadoop/share/hadoop/mapreduce/hadoop-mapreduce-examples-2.6.0-cdh5.8.2.jar pi 10 1000


git clone git://github.com/lintool/bespin

mvn clean package

mkdir data

curl http://lintool.github.io/bespin-data/Shakespeare.txt > data/Shakespeare.txt

curl http://lintool.github.io/bespin-data/p2p-Gnutella08-adj.txt > data/p2p-Gnutella08-adj.txtclean package

/usr/local/hadoop/bin/hadoop jar /usr/local/hadoop/bin/hadoop/target/bespin-1.0.5-SNAPSHOT.jar io.bespin.java.mapreduce.wordcount.WordCount -input data/Shakespeare.txt -output wc

# Parte 1


https://github.com/ThaisGabriele/bdg-pis.git

mvn archetype:generate -DgroupId=br.edu.ufam.ThaisGabriele -DartifactId=pi1p1

bdg-pis/pi1p1 nova versão pom.xml


mv bespin/src/main/java/io/bespin/java/mapreduce/wordcount/WordCount.java bdg-pis/pi1p1/src/main/java/br/edu/ufam/ThaisGabriele

Agora, no diretório base bdg-pis/pi1p1, rode o Maven para criar seu package:
$ mvn clean package

Depois que o build terminar com sucesso, deverá ser possível rodar o programa do contador
de palavras no seu próprio repositório:

/usr/local/hadoop/bin/hadoop jar target/pi1p1-1.0-SNAPSHOT-fatjar.jar br.edu.ufam.ThaisGabriele.WordCount -input data/Shakespeare.txt -output wc2 -reducers 5

------------------------------------------------------

# Projeto de Implementação 1 - Questões

### Questão 1. Qual é o primeiro termos no arquivo part-r-00000 e quantas vezes ele ocorre ?

a-breeding	1

É o termo "a-breeding". Ocorre uma vez.

### Questão 2. Qual é o terceiro termo antes do último em part-r-00004 e quantas vezes ele ocorre ?

zeals	1

### Questão 3. Quantos termos únicos existem?

* 00000 : 2516 termos unicos
* 00001 : 2567 termos unicos
* 00002 : 2438 termos unicos
* 00003 : 2520 termos unicos
* 00004 : 2623 termos unicos

**Modificando a Versão Original**


### Questão 4. Qual é o primeiro termos no arquivo part-r-00000 e quantas vezes ele ocorre?
a-breeding	1

### Questão 5. Qual é o terceiro termo antes do último em part-r-00004 e quantas vezes ele ocorre ?
zeals	1

### Questão 6. Quantos termos únicos existem?


