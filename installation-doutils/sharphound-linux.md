# Sharphound (Linux)

### Installation avec Docker

```
git clone https://github.com/fox-it/Bloodhound.py
cd Bloodhound.py
sudo docker build -t bloodhound .
docker run -v ${PWD}:/bloodhound-data -it bloodhound
```
