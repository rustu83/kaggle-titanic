## Kaggle titanic challenge

Je nekolik moznosti, jak vyvijet...
* V Pycharmu v dockeru vychazejicim z kaggle image.
    - Pycharm vypada trochu divne a nedokaze v notebooku vsechno dobre zobrazit
* V Pycharmu lokalne s pythonem z anacondy
    - Zobrazeni je lepsi, ale ne uplne dokonale. Pycharm ma trochu tendenci lagovat.
* V prohlizeci nebo primo na kagglu
    - Zobrazuje se nejlepe, ale zase neni oindexovano a nedaji se proklikavat pythoni funkce.

**Idealne z toho vychazi kombinace lokalniho Pycharmu a prohlizece.**

---------------------------------------------------------------------
---------------------------------------------------------------------
### Docker
##### Stahnout kaggle image
~~~
docker pull kaggle/python
~~~
##### Nebo vytvorit vlastni image nad nim
~~~
docker build -t my-kaggle/python .
~~~
##### Vytvorit container
- bude protunelovany port 8888 do hosta
- jupyter notebook je ale potreba poustet na ip 0.0.0.0, pokud ho chci videt v prohlizeci
~~~
docker run --name kaggle-python -h kaggle-python -e DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix -v $HOME:/host_home -p 8888:8888 -it my-kaggle/python
~~~
##### Nastartovat container, pokud stoji
~~~
docker container start kaggle-python
~~~
##### Pustit okno v bezicim containeru s bashem
~~~
docker exec kaggle-python -it /bin/bash
~~~
##### Pustit Pycharm s protunelovanyma Xkama
~~~
/host_home/path/to/pycharm/bin/pycharm.sh  > /dev/null 2>&1 &
~~~
--------
--------
### Lokalne
* Nainstalovat anacondu z installeru z https://repo.continuum.io/archive/
